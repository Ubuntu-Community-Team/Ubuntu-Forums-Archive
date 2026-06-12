---
title: "Failed to reinstall Grub"
date: 2008-07-02
forum: General Help
---

### Post by Xirowei on 2008-07-02
Recently i just format and reinstall Windows XP on Drive C.
Afterward i boot into Ubuntu Live CD and type below command:

[B]sudo grub
grub> find /boot/grub/stage1 (hd0,5)
grub> root (hd0,5)
grub> setup (hd0)
Checking if "/boot/grub/stage1" exists... yes
Checking if "/boot/grub/stage2" exists... yes
Checking if "/boot/grub/e2fs_stage1_5" exists... yes
Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded. succeeded
Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2/boot/grub/menu.lst"... failed Error 12: Invalid[/B]

But it failed in the last stage? Previously when i format and reinstall Windows XP on Drive C, if i follow above commands it can success reinstall the Grub. But this time it failed to reinstall the Grub. May i know what is my problem and how should i fix it?

---

### Post by arist0tle on 2008-07-03
Check out SuperGrub. It has helped me in several such circumstances. Just google it, download it, and burn it to a cd. It might take a minute to figure out, but it works really well.

---

### Post by VMC on 2008-07-03
Boot up using ubuntu livecd and type the following from a Terminal:

```
sudo fdisk -l
```

copy the info back here.

---

### Post by Xirowei on 2008-07-03
> **VMC said:**
> Boot up using ubuntu livecd and type the following from a Terminal:

```
sudo fdisk -l
```

copy the info back here.

ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5) 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14d614d5 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        3826    10249438+  83  Linux
/dev/sda6            3827        3989     1309266   82  Linux swap / Solaris
/dev/sda7            3990       19457   124246678+   7  HPFS/NTFS 

ubuntu@ubuntu:~$

---

### Post by VMC on 2008-07-03
Okay, so it looks like your ubuntu is on sda5. When you boot up, do you see a Grub booting menu?

```
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2008-07-03
> **Xirowei said:**
> ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5) 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x14d614d5 
Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19457   135805477+   f  W95 Ext'd (LBA)
/dev/sda5            2551        3826    10249438+  83  Linux
/dev/sda6            3827        3989     1309266   82  Linux swap / Solaris
/dev/sda7            3990       19457   124246678+   7  HPFS/NTFS 

ubuntu@ubuntu:~$
So is sda5 your Ubuntu partition I assume? If that is the case, you should be using (hd0,4) in Grub's World, not (hd0,5).

---

### Post by Xirowei on 2008-07-03
> **arist0tle said:**
> Check out SuperGrub. It has helped me in several such circumstances. Just google it, download it, and burn it to a cd. It might take a minute to figure out, but it works really well.

I had just using SUPER GRUB to FIX the Grub loading problem. Afterward, in Windows XP I installed "Ext2IFS_1_11.exe" to grant access to Ubuntu installation partition. I navigate to \boot\grub\menu.lst, open up menu.lst and correct the information from:

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		**(hd0,4)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=55a88a7e-1df4-4a44-bbbc-6fe536270423 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

To:
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		**(hd0,5)**
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=55a88a7e-1df4-4a44-bbbc-6fe536270423 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

Now i finally able to boot into Ubuntu from the Grub loading screen!

---

