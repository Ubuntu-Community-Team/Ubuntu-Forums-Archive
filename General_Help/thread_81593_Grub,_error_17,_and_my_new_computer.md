---
title: "Grub, error 17, and my new computer"
date: 2005-10-24
forum: General Help
---

### Post by chronusdark on 2005-10-24
Ok i have a brand new computer...AMD64 3000+

I installed windows xp ....worked fine.

Installed ubuntu wouldnt boot so i had to change my bios setting for my harddrive from Auto to LBA.

Then ubuntu worked...but then when i tried to boot to windows it hangs.

So i flipped my bios settings back to auto and now i get a grub error 17.

So i booted windows recovery console and did:

```
fixboot
fixmbr
```
Then my computer will boot windows fine but i have to go into ubuntu live and reinstall grub and change my bios back to LBA to get to linux.......can someone please help me!!!

parted partition info
```
(parted) p
Disk geometry for /dev/hda: 0.000-57241.898 megabytes
Disk label type: msdos
Minor    Start       End     Type      Filesystem  Flags
1          0.031  29999.812  primary   ntfs        boot
2      30004.211  56094.147  primary   ext3
3      56094.148  57239.406  extended
5      56094.179  57239.406  logical   linux-swap
```

fdisk partition info
```
Disk /dev/hda: 60.0 GB, 60022480896 bytes
16 heads, 63 sectors/track, 116301 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       60952    30719776+   7  HPFS/NTFS
/dev/hda2           60961      113970    26716095   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3          113970      116296     1172745    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5          113970      116296     1172713+  82  Linux swap / Solaris

```

Thanks in Advance!!!

---

### Post by chronusdark on 2005-10-25
figured out my prob....my /boot cant be past 1024 cylinders so i just put boot on another disk and now everything works great

---

