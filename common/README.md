This directory contains code that may be shared by different
components. Some pieces of code, for example, mongoose and the JS engine,
amalgamate common functions - therefore if they are compiled together, it
may result in link conflicts.

Therefore, functions in common/ are tagged as __attribute__((weak)),
which tells the linker to choose any (the first one?) suitable symbol.
Note that the tag should be put in the .c source, not in the header,
otherwise the buggy esp8266 linker will not link the FW properly.
