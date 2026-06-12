---
title: "Partition does not exist?"
date: 2007-07-19
forum: General Help
---

### Post by catnappist on 2007-07-19
I just snipped a 4Gb chunk off the end of a FAT32 drive and made it FAT16 in gparted, then rebooted, and guestimated an entry into fstab:

# /dev/hdb4
UUID=469E-9114  /media/hdb4     vfat    defaults,utf8,umask=007,gid=46 0       1

Everything after "/media/hdb4" is a copy of what a FAT32 partition said because I didn't know what else to insert.  A message in the boot says the partition doesn't exist.  ](*,)

Any idea how to fix fstab so it recognizes a 4Gb FAT16 partition?

Thanks!

---

### Post by merlinus on 2007-07-19
Did you manually create /media/hdb4?

What is the output of:

```

sudo fdisk -l

```

(l is a lowercase L}

-merlin

---

### Post by catnappist on 2007-07-19
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3320    26667868+   7  HPFS/NTFS
/dev/hda2            3321        9467    49375777+  83  Linux
/dev/hda3            9468        9729     2104515   82  Linux swap / Solaris

Disk /dev/hdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        9729    78148161    7  HPFS/NTFS
/dev/hdb2            9730       17633    63488880    7  HPFS/NTFS
/dev/hdb3   *       17634       29880    98374027+   b  W95 FAT32
/dev/hdb4           29881       30401     4184932+   6  FAT16

This is the only place I've seen the drive mentioned, it doesn't show up in nautilus.  When I'm booting I see one line that says something like "/media/hdb4 does not exist" and then a red "fail."

---

### Post by Ayuthia on 2007-07-19
At the begging of merlin's post he asked if you created /media/sda4.  Is that path there?  If not, it needs to be created.

---

### Post by taurus on 2007-07-19
```
sudo mkdir /media/hdb4
sudo mount -a
df -h
```

---

### Post by catnappist on 2007-07-19
:)  Damn, Taurus, you guys are friggin geniuses.  How'd you do that?  :)

:)

Thanks!

---

