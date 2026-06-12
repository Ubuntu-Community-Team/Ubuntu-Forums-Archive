---
title: "Scrub Disk"
date: 2020-09-28
forum: General Help
---

### Post by greatoffender on 2020-09-28
I have researched a few suggestions on completely removing all partitions from the drive but I want to make sure I get this right. Had Mint running on a brand new laptop for about 10 minutes before I think I messed it up. I keep getting integrity errors when I try and reload it after completely choosing "completely erase". Had to remove boot security on the drive to get it to start on the usb drive but always get the same end result "integrity ...". I did get it to launch with security once but I received errors about not finding the kernel. 

I would like to boot from the installation usb and then use the line command to remove it ALL. Any help would be appreciated. - Thanks

---

### Post by HermanAB on 2020-09-29
Howdy,

If you zero the first little bit of a disk, then all the partition table information is zapped and an OS installer program will see the disk as 'new'.

You can do this by booting with any Linux install media, then running a program like Data Definition, with which you can set the number of bytes to write to the disk.

For example:
*# dd if=/dev/zero of=/dev/sda count=1M*

Read the *dd *man page for more information on what it can do.

Alternatively, you can wing it with a program such as concatenate:
[I]# cat /dev/zero >/dev/sda
...count to ten...
Press Ctrl-C[/I]

---

### Post by ActionParsnip on 2020-09-29
[https://linuxhint.com/completely_wipe_hard_drive_ubuntu/](https://linuxhint.com/completely_wipe_hard_drive_ubuntu/)

---

### Post by metacell on 2020-09-29
You mean, you get integrity errors when trying to reinstall Ubuntu Mint on the drive?

Do you get any errors when erasing the drive?

---

### Post by greatoffender on 2020-09-29
> **metacell said:**
> You mean, you get integrity errors when trying to reinstall Ubuntu Mint on the drive?

Do you get any errors when erasing the drive?

Acer Inspire 5 - 2019 model SSD. I have tried installing several different ways to include reinstalling/erasing reinstalling. At this point I am starting to think it may be the chipset. It booted once and I updated only to have it boot to a black screen in every subsequent attempt. Every fresh install since has been to a black screen with integrity errors 55/56 (?).

---

### Post by greatoffender on 2020-09-29
> **HermanAB said:**
> Howdy,

If you zero the first little bit of a disk, then all the partition table information is zapped and an OS installer program will see the disk as 'new'.

You can do this by booting with any Linux install media, then running a program like Data Definition, with which you can set the number of bytes to write to the disk.

For example:
*# dd if=/dev/zero of=/dev/sda count=1M*

Read the *dd *man page for more information on what it can do.

Alternatively, you can wing it with a program such as concatenate:
[I]# cat /dev/zero >/dev/sda
...count to ten...
Press Ctrl-C[/I]

What I was looking for was something similar to the old DOS fdisk and completely wipe the drive and partitions to start over with a completely blank drive.

---

### Post by dinkidonk on 2020-09-29
> **greatoffender said:**
> What I was looking for was something similar to the old DOS fdisk and completely wipe the drive and partitions to start over with a completely blank drive.

Using the "dd" command will write zeros / null bytes onto the part of the drive where the partition table is located. Doing this will cause the drive to appear as a new drive even if much of the data is still on the drive.

```
*sudo dd if=/dev/zero of=/dev/sda bs=1M count=1*
```

This will erase the first megabyte of the physical drive "/dev/sda", and this is enough to kill all partitions and file systems.

---

### Post by greatoffender on 2020-09-29
I'm closing this. I have determined that there is an issue with the SSD as even Windows refuses to load back on the machine because of drive errors. It was new out of the box so less than 24 hours later it's back in the box and going far far away. This doesn't mean I don't appreciate the help because i do. Immensely. Thank you all for taking the time to respond to my post and hope I didn't waste your time. I did learn something.

---

