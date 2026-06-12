---
title: "Installed Windows XP. Not listed in GRUB?"
date: 2006-08-04
forum: General Help
---

### Post by kpkeerthi on 2006-08-04
I resized my partition with gparted and installed windows xp on a 50 GB partition that I created. XP overwrote MBR and I could not get on on ubuntu. I understand that this is expected and no problems here.

I then popped in ubuntu CD and booted Live and did:
```

> grub
> root (hd0,0)
> setup (hd0)
> quit

```
... and all was fine.

But when I reboot, I could NOT see Windows XP listed in the GRUB boot menu. Am I missing something here?

fdisk -l
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5099    40957686   83  Linux
/dev/sda2   *        5100       11665    52741395    7  HPFS/NTFS
/dev/sda3           11666       12161     3984120    5  Extended
/dev/sda5           11666       12161     3984088+  82  Linux swap / Solaris

Disk /dev/sdb: 1040 MB, 1040187392 bytes
32 heads, 32 sectors/track, 1984 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes

```

Is there a way I could get on to XP from GRUB menu? Appreciate your help.

---

### Post by kpkeerthi on 2006-08-04
Never mind. Got it working.

---

### Post by Refah on 2006-08-04
Hey, I'm glad you got it working - only you don't say how! I'm trying to reinstall windows as a backup to Ubuntu as well... Say, did you use your recovery cd or a windows xp cd?  - Refah

---

### Post by kpkeerthi on 2006-08-06
Add
```

title           Microsoft Windows XP Media Center Edition 2005
root            (hd0,1)
chainloader +1
boot

```
near the end of /boot/grub/menu.lst. Also uncomment **hidemenu** option so the GRUB menu shows up upon booting. 
The DVD that came with my notebook reads 'Windows Reinstallation DVD'. Don't really know if it is a recovery or an install CD... but it could do both.. LOL.

---

