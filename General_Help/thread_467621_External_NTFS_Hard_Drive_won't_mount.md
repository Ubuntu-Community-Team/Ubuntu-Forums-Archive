---
title: "External NTFS Hard Drive won't mount"
date: 2007-06-07
forum: General Help
---

### Post by DannyP487 on 2007-06-07
I was in the process of copying some files from an internal drive to my external, and I plugged a cord into one of my other USB ports, and apparently something shorted out-- my screen went black, my music stopped playing, but it didn't completely turn off my computer.

I wasn't able to do anything to get it back, so I forced it to shut down, and when it came back, it wasn't able to mount my external hard drive.  My other drives seem to be working fine.

I powered the external off, and when I turned it back on, I got an error saying it cannot mount the drive.  It then told me to either boot twice in windows, type 

sudo mount -t ntfs-3g /dev/sdb1 /media/My Book -o force

into the terminal, and to change a setting in fstab.  I didn't have any luck with anything.  Furthermore, when booting into windows, it could see my drive, but not the folder it was copying files to.

Any ideas? Thanks, it is much appreciated.

---

### Post by DannyP487 on 2007-06-08
anyone?

---

### Post by Pisi-Deff on 2007-06-08
> sudo mount -t ntfs-3g /dev/sdb1 /media/My Book
I think the problem could be the space
Try this: 
```
sudo mount -t ntfs-3g /dev/sdb1 /media/My\ Book
```

---

### Post by DannyP487 on 2007-06-08
I typed in the command:  sudo mount -t ntfs-3g /dev/sdb1 /media/My\ Book

and it returned:

Volume is scheduled for check. Please boot into Windows TWICE, or
use the 'force' mount option. For example type on the command line:

    mount -t ntfs-3g /dev/sdb1 /media/My Book -o force

Or add the option to the relevant row in the /etc/fstab file:

    /dev/sdb1 /media/My Book ntfs-3g defaults,force 0 0

I tried these options with no luck.

---

### Post by DannyP487 on 2007-06-08
Well, scratch that.... I rebooted in Windows another 2 times, and the drive DID decide to mount this time.  Go figure. However when I was checking it, it lost the entire folder I was copying files to.  The free space available shows that those files are still on the disc, but they are not there, and not in a hidden folder either.

---

### Post by xarmian on 2007-06-09
Boot in to windows, open a DOS window and type:

chkdsk d: /f

Where "d:" is, replace with the drive letter of the trouble NTFS drive.  This will force a file system check and should repair any problems.  You can also try ntfsfix within linux:

ntfsfix /dev/sdb1

But if you can run chkdsk I recommend trying that first..

-Dave

---

