---
title: "How do I force unmount?"
date: 2007-01-09
forum: General Help
---

### Post by theaverageidiot on 2007-01-09
I have this:
[http://ubuntuforums.org/showthread.php?t=276743](http://ubuntuforums.org/showthread.php?t=276743)
And it works fine, but I'm trying to install World of Warcraft which requires multiple discs. I'm stuck at the screen asking for disc 2 because I can't unmount disc 1 because the setup is open and it gives some access error. :(

I tried manually unmounting with force:
```
sudo umount -l/-f /media/cdemu0
```
I tried both -l and -f (at different times of course :/) and both had the same effect: it appeared to unmount cdemu0 but when I mounted disc 2 it put it at cdemu1 instead of cdemu0. WoW won't detect it from cdemu1, it has to be at cdemu0. And apparently it never unmounted because if I go to /media/cdemu0 it's still there and the label comes back up on my desktop.

Pleeeassseee someone help me :).

---

### Post by kebes on 2007-01-09
Hmm... That's a strange problem, for sure.


Something to consider: you could copy all the disks to your hard drive as ISO images, and then mount and unmount them. Use "mount -t iso9660" or "mount -o loop"... see examples:
[http://www.techspot.com/vb/topic483.html](http://www.techspot.com/vb/topic483.html)
[http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html](http://www.cyberciti.biz/tips/how-to-mount-iso-image-under-linux.html)
[http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.debianadmin.com/mount-and-unmout-iso-images-without-burning-them.html)

I'm not sure if this will make any difference or not... it might still complain about the program having a lock on the file. But you can mount the various disks to different places. Maybe the installer lets you "browse..." to the next disk?

---

### Post by kebes on 2007-01-09
> **theaverageidiot said:**
> 
sudo umount -l/-f /media/cdemu0

Another thought: could you mount to /media/cdemu0 and then create a symlink to that device:
cd /media/
ln -s /media/cdemu0 cdcurrent

Then do the install from "cdcurrent". Then mount the second cd to "cdemu1" or whatever. And then when it says "insert disk 2" can you force the symlink to change:
ln -s /media/cdemu1 cdcurrent

Maybe it will let you update the symlink while the installer is running?

---

