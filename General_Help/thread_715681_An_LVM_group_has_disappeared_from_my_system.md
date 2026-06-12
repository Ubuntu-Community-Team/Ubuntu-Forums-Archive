---
title: "An LVM group has disappeared from my system"
date: 2008-03-05
forum: General Help
---

### Post by runesvend on 2008-03-05
I have an old computer with some hard disks in it running Ubuntu at work. It hadn't been used in about a month previous to me starting it today. It has two LVM partitions from a previous Fedora installation. These to LVMs (VolGroup00 and VolGroup01) worked fine last time the computer was running, but now when I started the computer today VolGroup00 was gone!

The LVM that is gone is on partition hdc2. This is the output of *pvscan -vv*:

```
vektor@oldbackup:~$ sudo pvscan -vv
      Setting global/locking_type to 1
      File-based locking selected.
      Setting global/locking_dir to /var/lock/lvm
    Wiping cache of LVM-capable devices
    Wiping internal VG cache
    Walking through all physical volumes
      /dev/ram0: size is 131072 sectors
      /dev/ram0: size is 131072 sectors
      /dev/ram0: No label detected
      /dev/hda: size is 24901632 sectors
      /dev/hdc: size is 160086528 sectors
      /dev/VolGroup01/LogVol00: size is 489029632 sectors
      /dev/VolGroup01/LogVol00: size is 489029632 sectors
      /dev/VolGroup01/LogVol00: No label detected
      /dev/ram1: size is 131072 sectors
      /dev/ram1: size is 131072 sectors
      /dev/ram1: No label detected
      /dev/hda1: size is 21880467 sectors
      /dev/hda1: size is 21880467 sectors
      /dev/hda1: No label detected
      /dev/ram2: size is 131072 sectors
      /dev/ram2: size is 131072 sectors
      /dev/ram2: No label detected
      /dev/hda2: size is 3020220 sectors
      /dev/hda2: size is 3020220 sectors
      /dev/hda2: No label detected
      /dev/ram3: size is 131072 sectors
      /dev/ram3: size is 131072 sectors
      /dev/ram3: No label detected
      /dev/ram4: size is 131072 sectors
      /dev/ram4: size is 131072 sectors
      /dev/ram4: No label detected
      /dev/ram5: size is 131072 sectors
      /dev/ram5: size is 131072 sectors
      /dev/ram5: No label detected
      /dev/ram6: size is 131072 sectors
      /dev/ram6: size is 131072 sectors
      /dev/ram6: No label detected
      /dev/ram7: size is 131072 sectors
      /dev/ram7: size is 131072 sectors
      /dev/ram7: No label detected
      /dev/ram8: size is 131072 sectors
      /dev/ram8: size is 131072 sectors
      /dev/ram8: No label detected
      /dev/ram9: size is 131072 sectors
      /dev/ram9: size is 131072 sectors
      /dev/ram9: No label detected
      /dev/ram10: size is 131072 sectors
      /dev/ram10: size is 131072 sectors
      /dev/ram10: No label detected
      /dev/ram11: size is 131072 sectors
      /dev/ram11: size is 131072 sectors
      /dev/ram11: No label detected
      /dev/ram12: size is 131072 sectors
      /dev/ram12: size is 131072 sectors
      /dev/ram12: No label detected
      /dev/ram13: size is 131072 sectors
      /dev/ram13: size is 131072 sectors
      /dev/ram13: No label detected
      /dev/ram14: size is 131072 sectors
      /dev/ram14: size is 131072 sectors
      /dev/ram14: No label detected
      /dev/ram15: size is 131072 sectors
      /dev/ram15: size is 131072 sectors
      /dev/ram15: No label detected
      /dev/hdb: size is 490234752 sectors
      /dev/hdd: size is 488397168 sectors
      /dev/hdb1: size is 208782 sectors
      /dev/hdb1: size is 208782 sectors
      /dev/hdb1: No label detected
      /dev/hdd1: size is 488392002 sectors
      /dev/hdd1: size is 488392002 sectors
      /dev/hdd1: No label detected
      /dev/hdb2: size is 490014630 sectors
      /dev/hdb2: size is 490014630 sectors
      /dev/hdb2: lvm2 label detected
      /dev/hdb2: lvm2 label detected
      /dev/hdb2: lvm2 label detected
      /dev/hdb2: size is 490014630 sectors
    Fixing up missing format1 size (233.66 GB) for PV /dev/hdb2
  PV /dev/hdb2   VG VolGroup01   lvm2 [233.66 GB / 480.00 MB free]
  Total: 1 [233.66 GB] / in use: 1 [233.66 GB] / in no VG: 0 [0   ]
```

I don't understand why *pvscan* doesn't scan **hdc2** which is where the missing LVM resides.

I'm lost! :(

---

### Post by runesvend on 2008-03-05
That's strange. I worked with it a bit and decided to restart the computer because it had installed a new kernel. After the restart it worked fine :???:

Who knows what went wrong... It's solved anyway :)

---

