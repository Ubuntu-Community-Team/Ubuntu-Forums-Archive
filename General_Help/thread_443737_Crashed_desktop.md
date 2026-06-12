---
title: "Crashed desktop"
date: 2007-05-14
forum: General Help
---

### Post by Paul234 on 2007-05-14
I recently installed wubi on a 2 year old HP pavilion laptop for a friend. The install and setup was fast and painless, and after the initial reboot, i started installing some packages. Eventually, I was beginning to install some Java JDK packages when the computer froze. I left it alone for ten minutes, and when i came back, the fan stopped and the mouse/keyboard was frozen. I thought it was just a normal freeze, so I shut it down using the power key. I restarted it, and i got an error message saying something about loading BOOT.INI from the C:/windows directory. I then got a windows message about booting into safe mode (three varieties), the settings from the last time windows worked, or normal mode. All five modes result in some type of loading, a <1 sec flash of a variation of the blue screen of death, and a restart. The files on it are unavailible by using a Ubuntu live cd and accessing the disk, which worked before the crash. Please help me bring back the laptop!

---

### Post by ago on 2007-05-14
> **Paul234 said:**
> Eventually, I was beginning to install some Java JDK packages when the computer froze. I left it alone for ten minutes, and when i came back, the fan stopped and the mouse/keyboard was frozen.
Quite likely you run out of (virtual) disk space. Use a larger virtual disk if you plan to install a lot of stuff  

> I thought it was just a normal freeze, so I shut it down using the power key.
That is not generally a good idea, even less so when you run out of space (because you may end up shutting down while you have a file open in writing mode). Even if the keyboard freezes (X freezes), linux support Alt+SysRq key combinations (google for all key combinations)

That might well cause a corrupted ntfs (it may happen also if you hard boot windows while doing file r/w operations, it's not really a wubi specific issue). You need to use ntfs restore tools.  What happens when you try to access the partitions with ntfs-3g/ntfs?

---

### Post by Paul234 on 2007-05-14
would I access the drive with the ntfs tools using a live CD? I haven't reinstalled anything yet so i don't overwrite the files. 
Also, how do you increase the virtual disk size on wubi? Is this accessed from Windows?
btw, thanks for the alt+sysRq tip...i've been using ubuntu for a while but never knew that

---

### Post by tuxcantfly on 2007-05-14
if your windows is still working, you can just use toporesize (windows program) to resize the loopmounted partitions

[http://csemler.com/cs.html](http://csemler.com/cs.html)

---

### Post by Paul234 on 2007-05-14
Thanks, but that's the thing. Windows loads up to the startup screen, but after a second or two of the progress bar moving, it flashes the blue screen of death for a half-second and restarts. If I were to connect the hard drive to a working windows machine and used toporesize there, would it work?

---

