---
title: "External HDD Auto Mounting on Startup"
date: 2013-01-31
forum: General Help
---

### Post by abrand9 on 2013-01-31
I have two issues going on, they are probably related as i am still learning my way around linux.

I have a seagate external HDD formatted NTFS, it used to mount with r/w permissions and had no issues with it. After an upgrade it no longer would mount with r/w only read. Not a big deal, could re-mount with gparted or similar. Well i started to get lazy and thought I could have it automount with r/w permissions again. I believe added the drive information (UUID etc) to a config file (not sure which one it has been a while) and edited fstab with the following 

```
/dev/sdb1	/media/FreeAgent\040GoFlex\040Drive	ntfs	defaults,nls=utf8,umask=0222,nosuid,nodev	0	0
```  

Well now everytime my computer starts it tries to automount the external drive. My intended goal was just to mount with r/w permissions. So on startup i have to either skip the mount or manually mount by pressing 'S' or 'M'. I just created a bigger hassle for myself :(

My second, probably related, issue is every time i plug in a usb flash drive (FAT32) it tries to mount to the /media/FreeAgent location (the one created for the external drive). Which obviously doesn't work since it is not formatted NTFS. I did create a dir /media/flash and can mount there manually but again created a headache for myself.

So I am really looking for help on:
1. How do I stop the auto mounting of the external drive on startup
2. Prevent every flash drive from auto mounting to the /media/FreeAgent location. 

Any help is greatly appreciated, i tried working through it myself but am causing issues with my limited knowledge. Time to let the experts weigh in.

Thanks,

---

### Post by Bucky Ball on 2013-01-31
1. Delete the line to mount it in fstab.
2. Delete the /media/Freeagent mountpoint

Try this, restart and plug in a drive(s) and see what happens. Report back.

You don't mention the release you're using. Can I presume an older release?

---

### Post by abrand9 on 2013-01-31
Thanks Bucky for the quick suggestions. Did both and seemed to solve all my issues. External drive no longer tries to mount on startup and no problems with mounting flash drives formatted in FAT32.

Yep forgot to put my release, Vanilla Ubuntu 12.10. I believe my r/w issue happened in the transition from 11.04 to 11.10. 

Now my only question is how to mark as solved?

*edit- Found it, marked as solved

---

### Post by Bucky Ball on 2013-01-31
Thread Tools at top right and 'Mark thread as solved'.

Glad it all worked out and good luck with it. Make sure to post a new thread with any other issues. ;)

---

