---
title: "Problems getting Wine running on Edgy"
date: 2006-10-27
forum: General Help
---

### Post by zarathustra on 2006-10-27
I've just tried compiling and installing the latest Wine, 0.9.24, but when I try running winecfg I get a segmentation fault. I had this problem with 0.9.23 too. Is anyone else having a problem? What can I do to find out what's wrong?

---

### Post by PriceChild on 2006-10-27
Are you getting wine from the official ubuntu repos? or a bleeding edge unofficial one?

---

### Post by zarathustra on 2006-10-27
Using the source files from Sourceforge.

---

### Post by Protoss on 2006-10-27
I just tried compiling 0.9.24, to see if WoW performance would increase any, but it seg-faults for me too.
According to [https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965](https://launchpad.net/distros/ubuntu/+source/wine/+bug/56965) it has to do with GCC, and setting a CFLAG fixes it, but it doesn't seem to fix it, I set the CFLAG, re-run ./configure, make depend && make, then sudo make install but it still seg-faults.

---

### Post by zarathustra on 2006-10-27
Well it works with that compiler flag in a way. I get the error when winecfg starts up:

> Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Xlib:  extension "XFree86-DRI" missing on display ":0.0".


And I can't see to install anything with it.

---

### Post by T3h_Dohtem on 2006-10-28
> **zarathustra said:**
> Well it works with that compiler flag in a way. I get the error when winecfg starts up:



And I can't see to install anything with it.

If youre on ATI, check this page out. I might be way off, but theres something noted about ATI driver not being able to handle Composite with DRI (not sure what this means, but both the error, and the page listed say something about display extensions) and Edgy defaults to having it on.

[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
Good luck with that, hopefully it works, cause I just got edgy and am having the seg faults too. Keep us posted :D

---

### Post by zarathustra on 2006-10-28
Thanks, I had already Googled it since I wasn't sure whether I'd get a reply. I've managed to install a game, however I'm getting this error when trying to start it:

> err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135
err:module:import_dll Library ntoskrnl.exe (which is needed by L"C:\\windows\\system32\\drivers\\SECDRV.SYS") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\windows\\system32\\drivers\\SECDRV.SYS" failed, status c0000135


---

### Post by T3h_Dohtem on 2006-10-28
Hrmmm...cant help you there, but Ntoskrnl being missing is not a good sign. As for me, I still havent gotten past the compile issues. Im still getting a segfault when I try to run wine. Ive also noticed that when trying to get the dependencies (as listed on the winehq homepage) there are alot of errors. One required package conflicts with the dependencies on another package, and some stuff is just not being found. Being that Edgy just came out, and 0.9.24 just came out, I think we're gonna have some problems here :( Might just sit back and wait this one out.

---

### Post by spacyspacy on 2006-10-29
Try to configure with 
```
./configure -fno-stack-protector
```

---

### Post by DeemanXu on 2006-10-31
> **spacyspacy said:**
> Try to configure with 
```
./configure -fno-stack-protector
```

Am having the same problem as zarathustra, and i tried ya ./config idea, but unfortunately
i get the following error 

configure: error: unrecognized option: -fno-stack-protector

Oh well, am sure there's a solution out there somewhere for all us edgy-ites.

---

### Post by tempo500 on 2006-11-01
i think i have the same problem? i guesss i will wait untill the gurus find out whats going wrong. by the way i hadnt any dependancy issues with the recommend packages from wineHQ... phil
[http://www.ubuntuforums.org/showthread.php?t=289778&highlight=wine]("http://www.ubuntuforums.org/showthread.php?t=289778&highlight=wine")

---

### Post by distroman on 2006-11-01
I get segmentation fault with 0.9.24 as well, however 0.9.22 from the repo runs fine here.

---

### Post by reiki on 2006-11-01
> **DeemanXu said:**
> Am having the same problem as zarathustra, and i tried ya ./config idea, but unfortunately
i get the following error 

configure: error: unrecognized option: -fno-stack-protector

Oh well, am sure there's a solution out there somewhere for all us edgy-ites.

You'll get this error about -fno-stack-protector not being recognized if your gcc version is not 4.1. Previous gcc versions do not recognize that CFLAG. 

If you have gcc-4.1, try compiling with CFLAG="-fno-stack-protector -O2" (that's a letter O not a number 0)

Also... before you test your new wine, and assuming you have removed any previous version, rename your .wine directory and
then run winecfg so that your new wine creates a new .wine directory. Give those a try and please report back here as I am at work now and can't try this for another 8 hours or so at home.

---

### Post by zarathustra on 2006-11-01
I uninstalled the previously compiled Wine, and cleared the binaries out of the source folder before trying the new CFLAG, and it worked fine. I think the problem I am having now is something to do with the copyright software, so I'm not sure what I can do.

---

### Post by DeemanXu on 2006-11-01
Well, i tried the new solution, and it compiled alright, did make depend and make, then make install, then went to install it and i get a compile error - two, infact. I give up.

---

### Post by zarathustra on 2006-11-04
I'm getting a weird error now. The cursor doesn't appear in the application I'm running and I get this error over and over again:

> fixme:cursor:create_cursor Currently no support for cursors with 32 bits per pixel


The X server isn't even running in 32 bit mode.

---

### Post by zarathustra on 2006-11-05
I tried searching Wine's bug list to see if this has been reported. It has: [http://bugs.winehq.org/show_bug.cgi?id=5486](http://bugs.winehq.org/show_bug.cgi?id=5486).

I tried playing around with the emulation settings, and it seems to be running fine and showing the cursor with Windows 98, as the last comment on the bug report suggests.

---

