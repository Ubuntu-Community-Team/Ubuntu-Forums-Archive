---
title: "Can parted -l (print) Be Safely Used While Mounted?"
date: 2017-05-05
forum: General Help
---

### Post by jamoody on 2017-05-05
SMART is reporting pending sectors and I'd like to know what files are associated to them.  I'm trying to generally follow [https://www.smartmontools.org/wiki/BadBlockHowto](https://www.smartmontools.org/wiki/BadBlockHowto) to do this.  I'm actually running mostly JFS filesystems so I'll have to adjust most commands for that.

 I have the LBA (which I assume is decimal) from GSmartControl and want to use parted to see what partition it is in (for starters).  Can parted -l (print from the menu) be safely used on a mounted file system?  I assume I should use menu command "unit s" before "print" to get the layout in sectors so I can compare to the LBA which I also assume is sectors.

According to the above writeup once I have the partition I'll then move on to finding the block size using (in my case) "jfs_tune -l", calculate the block number, use jfs_debugfs to identify the associated inode and finally the file.  I assume these commands can be safely done while mounted as well.

Any cautions/concerns (other than don't delete/create/resize etc partitions) doing all this with a mounted filesystem?  Thanks.

---

### Post by frostschutz on 2017-05-06
parted -l and other readonly operations are safe.

you can also write it like 'parted /dev/disk unit s print free' which is also safe.

if you want to make really extra sure... you could create a readonly loop device on top and run parted on that. or use snapshot overlays, there's a page in the linux raid wiki about those.

---

