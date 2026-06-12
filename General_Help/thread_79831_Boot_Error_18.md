---
title: "Boot Error 18"
date: 2005-10-20
forum: General Help
---

### Post by OhSqueezy on 2005-10-20
Hi, I'm hoping that somebody can help me out with a problem I'm having... On startup, I'm receiving this error: "Error 18: Selected cylinder exceeds maximum supported by BIOS".  The machine is a Pentium II 233Mhz.

This also appears:
root(hd0,0)
Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash

From the research I've done so far, I've gathered that this has something to do with a partition being too large (?) and I'm guessing I have to edit that, but I'm not sure how to do that.  I'm also not sure if that's what I'm supposed to do.  It seems as if I have only two partitions: one 19.8 GB, one 200 MB.  

Ubuntu had been running fine for a month beforehand.  Any help would be appreciated.  As you can see, I'm new.

---

### Post by OhSqueezy on 2006-01-26
In case anybody comes across this post in an attempt to fix a similar issue, my solution was to re-partition the hard drive with a small /boot partition (1 GB), a giant partition for everything else (18.8 GB), and a swap partition (.2 GB).  That's basically the defaults for Ubuntu with an added boot partition.

I couldn't figure out a way to fix the problem and save my files, but I transfered most of them off using FTP and a system restore CD before re-partitioning.  Also, the first time I tried re-installing, I got the same grub error (18) and I still couldn't boot Ubuntu even though I reformated the hard drive, so make sure your boot partition is small and at the beginning of your hard drive (it has to be within a certain number of cylinders, apparently).

My server has been working fine now for a week, and I've rebooted at least once a day with no problems.  Be aware, however, that these are just suggestions from somebody who had no idea what they were doing.

---

