---
title: "Wine &amp; Dreamweaver 8 Help"
date: 2006-10-01
forum: General Help
---

### Post by jazee on 2006-10-01
I have been following this tutorial [http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/09/04/how-to-dreamweaver-and-flash-8-running-on-ubuntu-dapper/)
 to get dreamweaver 8 to run on my Ubuntu Dapper Drake install.

But for some reason during the splash screen load it crashs out at the "Initializing Files" portion of the load. The message I get back from Wine is:
```

fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f7d0,0x00000000), stub!
fixme:ole:CoRegisterMessageFilter stub
wine: Unhandled page fault on read access to 0x000007e0 at address 0x7e0 (thread 0009), starting debugger...
WineDbg starting on pid 0x8
Unhandled exception: page fault on read access to 0x000007e0 in 32-bit code (0x000007e0).

```

After that it goes throught and spits out stack and the register dumps.

Does anyone have any idea as to why this happens and how to fix it.

---

### Post by yopnono on 2006-10-02
Well I just installed it like normal, execute the DW installer. And entered the serial and of you go.

Dreamweaver 8 
Wine 0.9.21
Dapper

EDIT:
Updated to wine 0.9.22, works fine.

---

### Post by jazee on 2006-10-02
Ok I deleted the other version of Wine I had installed and added the repository that was listed on Wine HQ. Did the "apt-get update" and "apt-get install wine". After which I then tryed to run the installer for Dreamweaver at the prompt with "wine Desktop/Dreamweaver8.exe"  but when the install run it begins to write out error messages with the OpenGL GTK.

```

err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problem s
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e521fc0 "x11drv_main.c: X11DRV_C ritSection" wait timed out in thread 002c, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7e654fc0 "x11drv_main.c: X11DRV_C ritSection" wait timed out in thread 001e, blocked by 000e, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7ebfa820 "gdiobj.c: GDI_level" wa it timed out in thread 0020, blocked by 002c, retrying (60 sec)
nick@fury:/etc/apt$ err:ntdll:RtlpWaitForCriticalSection section 0x7ebfa820 "gdi obj.c: GDI_level" wait timed out in thread 0020, blocked by 002c, retrying (60 s ec)
err:ntdll:RtlpWaitForCriticalSection section 0x7effcce4 "loader.c: loader_sectio n" wait timed out in thread 0027, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7effcce4 "loader.c: loader_sectio n" wait timed out in thread 002a, blocked by 0020, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7effcce4 "loader.c: loader_sectio n" wait timed out in thread 002b, blocked by 0020, retrying (60 sec)

```

Any Ideas as to why this is doing this.

---

### Post by yopnono on 2006-10-03
Have no idea, but try to delete the .wine folder in your home directory and try again. Search for all your wine folders, even the hidden once and remove them.

Are you using compiz or something like that.

---

### Post by jazee on 2006-10-04
I deleted the .wine folder, uninstalled and reinstalled wine several time and I keep getting the same message. I even when throught and pretty much installed every library related to GLX and Xlib. Still nothing.

```

Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:advapi:CheckTokenMembership ((nil) 0x1690e8 0x34e794) stub!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
fixme:ole:ITypeInfo_fnRelease destroy child objects
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
Xlib:  extension "GLX" missing on display ":0.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
err:wgl:has_opengl Intialization of OpenGL info failed, disabling OpenGL!
err:ntdll:RtlpWaitForCriticalSection section 0x7e521fc0 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 002e, blocked by 0021, retrying (60 sec)

```

No I don't have anything special installed like compiz.

Any other ideas that might work for me.

---

### Post by yopnono on 2006-10-04
It's something to do with the graphic driver.
Have you tried to un/reinstall the graphic.

I did find something about graphic and a patch.
[http://appdb.winehq.org/appview.php?iVersionId=5606](http://appdb.winehq.org/appview.php?iVersionId=5606)

And some tip.
[http://www.daniweb.com/techtalkforums/thread1826.html](http://www.daniweb.com/techtalkforums/thread1826.html)

---

### Post by yopnono on 2006-10-17
Did you get it sorted? If not try to use wine regedit and delete all macromedia settings and you macromedia folder in you user profile.

And try this.
[http://bugs.winehq.org/show_bug.cgi?id=5304](http://bugs.winehq.org/show_bug.cgi?id=5304)

---

### Post by jazee on 2006-10-20
Na I haven't managed to get this to work. I tryed deleting everything and still keep having problems. But I will give that a try when I get sometime again to mess with it.

---

### Post by LetsLinux on 2006-10-20
I managed to get both Dreamweaver and Fireworks to with Wine in Dapper.

Check out my [my post]("http://www.ubuntuforums.org/showthread.php?t=266627") here on Ubuntu Forums. There is also a more detailed solution linked in the post.

Good luck
Jonas

---

### Post by factotum218 on 2006-10-20
Is GLX even running? Is it commented out on your xorg.conf or something?
Just a thought.

---

