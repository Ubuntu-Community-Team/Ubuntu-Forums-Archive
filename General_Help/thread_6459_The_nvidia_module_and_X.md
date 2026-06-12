---
title: "The nvidia module and X"
date: 2004-11-28
forum: General Help
---

### Post by karih on 2004-11-28
Hello, first post here so please be kind : ).

I have been trying to get the nvidia modules to work with XFree for the whole weekand and getting a bit tired :/.  

I am running kernel 2.6.8.1 (compiled my own) and have run the NVIDIA installer (downloaded latest from their webpage), which compiled the module and I can in fact do "modprobe nvidia" and the module loads.  Then after changing from "nv" to "nvidia" in the XFree config file, X will not start.

[Here](http://nfmh.is/~kari/pub/XFree86.0.log.error) is the output of the XFree86.log file, and the end of it is as follows:
```

...

(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xD0000000
(--) NVIDIA(0): MMIO registers at 0xE6000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

...
```I haven't got what to do so any help is well appreciated.

Then since this being my first post I must congratulate everyone behind Ubuntu for this great distro.  I expected much from it and wasn't disappointed.

Thanks in advance.

---

### Post by wallijonn on 2004-11-29
did you install libGLCORE.a? 
file:///usr/X11R6/lib/modules/extensions/libGLcore.a

---

### Post by Choi on 2004-11-29
[QUOTE=wallijonn]did you install libGLCORE.a? 
file:///usr/X11R6/lib/modules/extensions/libGLcore.a[/QUOTE]


Im missing that file aswell...  Got the same problem.
How/where do I get that file??  


Thanks!

---

### Post by karih on 2004-11-29
[QUOTE=wallijonn]did you install libGLCORE.a? 
file:///usr/X11R6/lib/modules/extensions/libGLcore.a[/QUOTE]
Not to my knowledge, no, and the file isn't there. 
However, I found libGLcore.so.1 in /usr/lib, is there some connection between these two?  I tried moving the file to /usr/X11R6/lib/modules/extensions/ and even rename it to the .a extension but neither worked.

Any idea how to fix this?

---

### Post by wschris on 2004-12-05
try "modprobe nvidia" (as root) after exiting from gdm, i had to do that after installing nvidia drivers manually (not through a deb package in synaptic)

unfortunately, everytime I reboot I have to wait until gdm autoloads and fails, then modprobe nvidia and startx again, I haven't found anywhere to add the option to automatically start the nvidia module at runtime

---

### Post by karih on 2004-12-05
[QUOTE=wschris]try "modprobe nvidia" (as root) after exiting from gdm, i had to do that after installing nvidia drivers manually (not through a deb package in synaptic)

unfortunately, everytime I reboot I have to wait until gdm autoloads and fails, then modprobe nvidia and startx again, I haven't found anywhere to add the option to automatically start the nvidia module at runtime[/QUOTE]Ah ok, it works for me too, thanks!
And to let the module be loaded at boot time, just add a line for it in the /etc/modules file.
Cheers! :)

---

