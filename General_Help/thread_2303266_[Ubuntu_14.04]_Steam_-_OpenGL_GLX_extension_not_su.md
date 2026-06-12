---
title: "[Ubuntu 14.04] Steam - OpenGL GLX extension not supported by display"
date: 2015-11-17
forum: General Help
---

### Post by Tomsen1410 on 2015-11-17
I have a problem with Steam on Ubuntu 14.04. Whenever I try to start steam I get the error message: "OpenGL GLX extension not supported by display".
When I try to start steam via the terminal, I also get this:


```
Running Steam on ubuntu 14.04 64-bit
STEAM_RUNTIME is enabled automatically
Installing breakpad exception handler for appid(steam)/version(1447125378)
Installing breakpad exception handler for appid(steam)/version(1447125378)
Installing breakpad exception handler for appid(steam)/version(1447125378)
OpenGL GLX extension not supported by displayAssert( Assertion Failed: Fatal Error: OpenGL GLX extension not supported by display ):Main.cpp:307


Installing breakpad exception handler for appid(steam)/version(1447125378)
assert_20151117163627_5.dmp[13238]: Uploading dump (out-of-process)
/tmp/dumps/assert_20151117163627_5.dmp
assert_20151117163627_5.dmp[13238]: Finished uploading minidump (out-of-process): success = yes
assert_20151117163627_5.dmp[13238]: response: CrashID=bp-3c7389d4-cb54-4fdb-a40d-ed31f2151117
assert_20151117163627_5.dmp[13238]: file ''/tmp/dumps/assert_20151117163627_5.dmp'', upload yes: ''CrashID=bp-3c7389d4-cb54-4fdb-a40d-ed31f2151117''

```




glxinfo is giving me:


```

Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
Xlib:  extension "GLX" missing on display ":0".
...and so on...

```




Also, when I open sysinfo->NVIDIA->OpenGL/GLX Information it says:


Failed to query the GLX server vendor.
I have a NVIDIA Quadro K2100M, Driverversion: 346.46

---

