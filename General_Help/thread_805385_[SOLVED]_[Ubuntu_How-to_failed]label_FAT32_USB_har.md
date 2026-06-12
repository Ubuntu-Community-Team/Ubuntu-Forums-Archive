---
title: "[SOLVED] [Ubuntu How-to failed]label FAT32 USB hard drive"
date: 2008-05-23
forum: General Help
---

### Post by kakyoism on 2008-05-23
I want to relabel my USB harddrive.
It's a FAT32.

I followed this link and it didn't work,
when I input:
sudo mlabel -i /dev/sda2 ::my-ipod

Here is the result:
"no directory slots"

Any ideas?

---

### Post by kpkeerthi on 2008-05-23
Which link did you follow?

---

### Post by kpkeerthi on 2008-05-23
Are you sure /dev/sda2 is your iPod?

---

### Post by kakyoism on 2008-05-23
Sorry, this one~~:
[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

BTW: I noticed that my disk is actually a fuseblk, so that means it's an NTFS??

Then I tried the *ntfslable*, with:
sudo ntfslabel /dev/sdc1 usb-label

then I got:
Access is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.
You can use force option to avoid this check, but this is not recommended
and may lead to data corruption.

Please help, I'm stuck !!

---

### Post by kakyoism on 2008-05-23
I just tried the option -f, here is the result:

[https://help.ubuntu.com/community/RenameUSBDri](https://help.ubuntu.com/community/RenameUSBDri)
~$ sudo ntfslabel -f /dev/sdc1 usb-download
Forced to continue.
Error opening partition device: Device or resource busy.
Failed to startup volume: Device or resource busy.
Failed to mount '/dev/sdc1': Device or resource busy.
Access is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by kakyoism on 2008-05-23
I checked, nothing is using that drive...

why is it constantly busy??

btw: how to use fuser to check it?

---

### Post by kpkeerthi on 2008-05-24
'forcing' an operation may lead to data loss. Don't do it. 
Can you post the output of ```
sudo fdisk -l
```?

---

### Post by kakyoism on 2008-05-24
Here it is:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0a53ace1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29271   235119276   83  Linux
/dev/sda2           29272       30401     9076725    5  Extended
/dev/sda5           29272       30401     9076693+  82  Linux swap / Solaris

Disk /dev/sdf: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2c48087c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       30515   245111706    c  W95 FAT32 (LBA)

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x936863ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641    c  W95 FAT32 (LBA)

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7e8f6eb7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xabfbc285

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    c  W95 FAT32 (LBA)

---

### Post by kakyoism on 2008-05-24
/dev/sdc1 is the one I was trying to label

---

### Post by motoperpetuo on 2008-11-30
hey, kakyoism, i was having the same problem you were having here renaming a flash drive formatted to NTFS. same errors about the volume being "already exclusively opened" and such. then i realized that i was trying to run ntfslabel on a mounted volume. i unmounted my flash drive before running the following:

```

sudo ntfslabel /dev/sdb1 moltar

```

and now my flash drive is called "moltar" (which sounds much better than "16.0 GB Drive"). not sure if this is the problem you were having, but i didn't see you specifically mention unmounting your flash drive before attempting to rename, so i figured i'd post it.

---

### Post by kakyoism on 2008-11-30
Ah, I'm an idiot!
Thank you so much for answering this after so long!!

---

