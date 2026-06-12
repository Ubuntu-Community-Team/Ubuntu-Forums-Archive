---
title: "Errors running .exe in wine"
date: 2006-10-14
forum: General Help
---

### Post by ryan76 on 2006-10-14
I'm trying to run a windows version of Risk that only has one file, an exe, and am getting these messages:

```
ryan@ryan-desktop:~/c/Program Files/Domination$ wine domin_v2.exe
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x608f6fc0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 000c, blocked by 000b, retrying (60 sec)wine: Critical section 608f6fc0 wait failed at address 0x602ad040 (thread 000c), starting debugger...
Modules:
Cannot get info on module while no process is loaded
Threads:
process  tid      prio (all id:s are in hex)
0000000d
        0000000e    0
0000000a (D) (null)
        0000000c    0
        0000000b    0
wine client error:b: write: Bad file descriptor
ryan@ryan-desktop:~/c/Program Files/Domination$

```

Can anyone help please? I can post outputs if needed.

Thanks

---

### Post by ryan76 on 2006-10-15
anyone...?

---

### Post by jincast90 on 2006-10-15
> **ryan76 said:**
> anyone...?

Should it be compatible with wine? Wine is not a miracle program which suddenly will run all your .exe files. It still has quite a long way.

---

