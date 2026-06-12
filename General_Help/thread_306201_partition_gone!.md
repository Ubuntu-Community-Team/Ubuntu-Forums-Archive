---
title: "partition gone!"
date: 2006-11-24
forum: General Help
---

### Post by fulv on 2006-11-24
I ended up with an ubuntu installation on a partition that appears as an "unknown filesystem".  is there any way to recover the data from that partition?

long story:
I had dapper installed on a logical ext3 partition, for dual-boot with XP on the primary (NTFS), and all was fine.  then I decided I wanted more space on the ext3 partition, but gparted would not allow me to resize anything (all the controls were disabled), so I booted from a utility CD, and ran PartitionMagic.  I shrunk the NTFS partition and the extended one, as well as   growing the ubuntu logical ext3 partition, and rebooted.

:mad: suddenly, grub failed to start!  so here I was without being able to either boot to XP, or to ubuntu!

so I went back to the live CD:  now, the original ext3 partition showed up as "unknown filesystem" or "unformatted" file system...  the additional space that I obtained by growing the extended partition somehow still appeared as unassigned, even though I thought I had resized the ext3 partition, too.

Anyway, I formatted that unassigned space, and re-installed dapper there, and now I'm back up, with grub allowing me back into XP and the new ubuntu installation.

however,  the original installation still shows up as "unformatted".

is there any way to recover the data from that partition, or should I just write it off?

how should I have resized that partition in the first place, in order not to loose it?

thanks!

---

