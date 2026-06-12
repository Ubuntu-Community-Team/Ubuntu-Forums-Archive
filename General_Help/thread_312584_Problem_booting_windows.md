---
title: "Problem booting windows"
date: 2006-12-04
forum: General Help
---

### Post by Repabil on 2006-12-04
I've got problems booting windows 2000 with grub. When I try to boot it it says> rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1and nothing else happens.

Here's output from fdisk -l /dev/hda:```
Disk /dev/sda: 320,0 GB, 320072933376 byte
255 huvuden, 63 sektorer/spår, 38913 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1               1       30394   244139773+  83  Linux
/dev/sda2           30395       30655     2096482+  82  Linux växling / Solaris
/dev/sda3   *       30656       38913    66332385    7  HPFS/NTFS
```
The lines for windows 2000 in my /boot/grub/menu.lst is:```
title           Microsoft Windows 2000 Professional
rootnoverify    (hd0,2)
savedefault
makeactive
chainloader     +1
```
I've tried using what the grub manual says [about booting windows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows). I've also tried copying my windows partition to first partition on a ide drive and doing FIXMBR in a repair console on a windows cd.

---

### Post by Repabil on 2006-12-04
I've also looked through [Bug #10661](https://launchpad.net/distros/ubuntu/+source/grub-installer/+bug/10661) and tried mentioned methods without success.

---

### Post by Repabil on 2006-12-07
Anyone got a clue? I'm banging my head against the wall here. Can it be windows not wanting to boot off of a S-ATA hdd?

---

