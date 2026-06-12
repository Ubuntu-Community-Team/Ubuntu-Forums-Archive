---
title: "Cannot kill processes in order to unmount disk"
date: 2014-03-06
forum: General Help
---

### Post by gannonlawlor on 2014-03-06
Hello,

I am trying to unmount the main disk in order to partiation it to get rid of the empty space on the main partiation. To do this I need to unmount the disk, I tried unmounting in disks and I was met with this error 

```
Error unmounting /dev/sda1:Command-line 'umount "/dev/sda1" exited with non-zero exit status 1: umount:/: device is busy.
(in some cases usful info about the processes that use the device is found by lsof(8) or fuser(1)) 
(udisks-error-quark, 14)
```

So after that error I ran ```
 sudo fuser -mv /dev/sda1 
``` as you can see some of the output in the picture below, then I ran ```
 sudo fuser -mu /dev/sda1 
``` and you can see that output below in the picture also. Any help would be much appreciated.[ATTACH=CONFIG]250902[/ATTACH]

---

### Post by Bashing-om on 2014-03-06
gannonlawlor; Hi Welcome to the forum .

One can not (UN)mount a file system that is presently inuse. So, what to do, what to do ?

Boot from the liveDVD and perform all your disk operations from the booted alternate operating system ( make sure that the liveDVD is not using the swap partition on the hard disk [gparted will show and allow to disable swap, if that is the case]) .
GParted is available on the desktop liveDVD.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

