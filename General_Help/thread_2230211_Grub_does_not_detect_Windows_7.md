---
title: "Grub does not detect Windows 7"
date: 2014-06-18
forum: General Help
---

### Post by obake2 on 2014-06-18
Hello everyone. I just installed Linux Mint 17 in one of my family computers and it so happens that GRUB didn't detect Windows 7 installation, so the computer just straight goes to boot Linux Mint. I didn't delete the Windows partition. What should I do? 

Thank you for your help guys in advance. ^_^

EDIT:

```
sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3272c242

Device          Boot    Start                   End                   Blocks                  Id      System
/dev/sda1       *        2048                  206847             102400                7       HPFS/NTFS/exFAT
/dev/sda2                 206848             508753756       254273449+      7       HPFS/NTFS/exFAT
/dev/sda3                 915333120      976771071       3078976             7       HPFS/NTFS/exFAT
/dev/sda4                 508755966      915333119       203288577        5       Extended
/dev/sda5                 508755968      906945421       199094727        83     Linux
/dev/sda6                 906946560      915333119       4193280             82     Linux swap / Solaris

Partition tables entries are not in disk order

```[/CODE]

---

### Post by Bashing-om on 2014-06-18
obake2; Hi !

Appears Windows is still there, we just need to make Mint aware that Windows exists.

Boot up mint to a terminal:
try terminal command:
```

sudo update-grub

```

reboot; the Windows boot option should now be available in grub's boot menu.
Please advise on the results.

[INDENT]ain't no step for a stepper
[/INDENT]

---

