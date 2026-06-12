---
title: "Force Mounting NTFS"
date: 2008-01-16
forum: General Help
---

### Post by Bendrx on 2008-01-16
I've looked around and still can't get this drive to mount. I unplugged it at work unsafely and now because wasn't unmounted in windows right I can't get it to load. Here's what I've been trying:

sudo mount -t ntfs-3g /dev/sda1 /media/New\ Volume -o force

I've also tried a couple variations from looking at the fourms here. I'll keep looking but if anyone has any ideas I would appreciate the input. 

I'm running Gutsy and thus far I've failed at forcing any drive to mount. Windows has a habit of making me irate so I had this problem alot when I was dual booting but always ending up just loading it back and shutting down proper like. Currently I have no windows installation, I will try booting up my Bart PE disk if I can't get this to work.

Thanks

---

### Post by geirha on 2008-01-16
What error message do you get with the mount-command above?

---

### Post by bodhi.zazen on 2008-01-16
First, make sure the mount point exists.

Then add this to /etc/fstab:

> /dev/sda1 /media/New\ Volume ntfs-3g defaults,force 0 0

Then 

sudo mount /dev/sda1

*seems to work from fstab and not the command line

---

### Post by geirha on 2008-01-16
/etc/fstab won't handle that escaped space "\ " in the mount-point. It must be replaced with \040 (the octal number for the space character). So:
```
/dev/sda1 /media/New\040Volume ntfs-3g defaults,force 0 0
```

---

### Post by Rwild on 2008-01-16
Still learning about everything myself... But I just had a problem like yours... Browse through the code in [this thread]("http://ubuntuforums.org/showthread.php?t=669462") if you please.  That's all I've got for you. ;)

---

### Post by crunchfighter on 2008-01-17
I had a similar problem with a bootable windows partition on my hard drive.  I had a gooned up shutdown from windows.  The mount command wouldn't work.  I had to reboot into Windows (sure enough - Windows told me I had a bad shutdown).  After that, the drive mounted in Ubuntu on its own

I recommend you plug your drive back into your Windows machine, shut it down right, and try it again with Ubuntu.

---

