---
title: "Wine wants OpenGL for everything... then fails"
date: 2007-01-26
forum: General Help
---

### Post by sdhoigt on 2007-01-26
Wine is hosed on my Edgy install.  It was working fine on Dapper, and I'm not sure if I tested Wine since upgrading to Edgy last month.

Anyway, no matter what I try to run I get something like this (running notepad in this example) and the program fails to launch:
```
$ notepad
wine: creating configuration directory '/home/dit/.wine'...
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Failed to open the service control manager.
err:wgl:X11DRV_wglGetProcAddress No libGL on this box - disabling OpenGL support !

```

I don't run any kind of 3D acceleration, so I'm completely confused by this output.  I've tried blowing away my ~/.wine directory but to no avail.

Any pointers would be very welcome.

Thanks!
SD

---

