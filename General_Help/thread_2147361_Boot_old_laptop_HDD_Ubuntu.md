---
title: "Boot old laptop HDD Ubuntu"
date: 2013-05-21
forum: General Help
---

### Post by AbbottSquared on 2013-05-21
After the graphics card on one of my laptops failed, I pulled the HDD out and have been trying to boot from it to get the files through a usb to sata connection.  It had been dual-booted with Windows 7/Vista and Ubuntu 12.04. 

I had mounted it as an external and could view all the files from Windows, and the Ubuntu OS files, but my home directory in Ubuntu seems to be encrypted.  My log-in password won't decrpyt it.

So, I've been trying to boot from that HDD, so to log-in to the directory, but to no avail.

If I move it to first priority at BIOS, loading grub from the now external hard drive, I get the errors:
```
error: invalid environment block
error: invalid magic number
error: you need to load the kernel first
```

If I load grub from my internal hard drive (dual-booted with Ubuntu 12.04 and Windows XP), after running ```
grub-mkconfig
``` with the external HDD plugged in and rebooting, I get the errors:
```
error: invalid magic number
error: you need to load the kernel first
```

There's an added difficulty that there is no CD drive on this laptop, so no LiveCD to help.

I'd greatly appreciate any direction on how to best accomplish this, or to know if its possible!  Thanks!

---

### Post by VMC on 2013-05-21
With the external hard drive plugged in, from a terminal type the following,so we can view he structural:

```
sudo fdisk -l
```

---

### Post by AbbottSquared on 2013-05-21
Here is the output of: ```
 sudo fdisk -l
```

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6e762533

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   302246909   151123423+   7  HPFS/NTFS/exFAT
/dev/sda2       302246910   312496379     5124735   1c  Hidden W95 FAT32 (LBA)
/dev/sda3       312496380   312576704       40162+  ef  EFI (FAT-12/16/32)

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x89900f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   201620221   100809087    7  HPFS/NTFS/exFAT
/dev/sdb2       598079488   625139711    13530112    7  HPFS/NTFS/exFAT
/dev/sdb3       201621502   598079487   198228993    5  Extended
/dev/sdb5       201621504   590219263   194298880   83  Linux
/dev/sdb6       590221312   598079487     3929088   82  Linux swap / Solaris

Partition table entries are not in disk order

```

(/dev/sda is the internal)

---

### Post by VMC on 2013-05-21
"[COLOR=#000000]but my home directory in Ubuntu seems to be encrypted" I'm not sure what this means. Did you encrypt your home volder when you installed Ubuntu?

Also sdb5 should be where your Ubuntu install is. You can't just mount it and read your /home folder?[/COLOR]

---

### Post by AbbottSquared on 2013-05-21
I didn't set up any encryption, but my personal directory in /home is encrypted now.  

I have mounted it and can read the /home directory, but not my personal directory because of the encryption.  Hence why I was trying to boot from it instead.

---

### Post by VMC on 2013-05-21
See if this [link]("http://www.theirishpenguin.com/2010/09/26/accessing-your-encrypted-home-directory-in-ubuntu.html") will help solve your dilemma.

---

