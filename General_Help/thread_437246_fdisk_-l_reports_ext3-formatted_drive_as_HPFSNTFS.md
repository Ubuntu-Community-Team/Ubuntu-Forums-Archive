---
title: "fdisk -l reports ext3-formatted drive as HPFS/NTFS"
date: 2007-05-08
forum: General Help
---

### Post by atarax on 2007-05-08
Finally got around to reformatting my 2nd hard drive (originally formatted as NTFS on my old Windows system) as ext3 - backed everything up and reformatted it using Disks Manager (just one big partition). I edited the device line in fstab to read:

/dev/hdb1 /media/storage ext3    defaults        0       0

and rebooted, it came up fine: I had to change the permissions to be able to write to the mount folder, but now I can copy files back to it. My only slight concern is that 'sudo fdisk -l' reports:

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19457   156288321    7  HPFS/NTFS

For all the ext3 partitions on hda, the System type is "Linux". Since it *seems* to be working fine, I guess this shouldn't bother me, but I don't want it to cause problems further down the line (especially if I start putting data on it that I don't have backed-up). Should I just ignore it? :confused: Thanks for any feedback!

---

