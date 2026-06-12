---
title: "misaligned partition"
date: 2013-04-04
forum: General Help
---

### Post by stephenbbb on 2013-04-04
I see this in disk utility. how do I fix it??
[ATTACH=CONFIG]240953[/ATTACH]

[http://www.flickr.com/photos/94409402@N02/8620225074/](http://www.flickr.com/photos/94409402@N02/8620225074/)

thanks everybody.

---

### Post by conradin on 2013-04-04
Have a look at this:
[http://askubuntu.com/questions/55214/how-do-i-correctly-align-partions-on-a-hdd-with-sector-size-of-4096-bytes](http://askubuntu.com/questions/55214/how-do-i-correctly-align-partions-on-a-hdd-with-sector-size-of-4096-bytes)

---

### Post by oldfred on 2013-04-04
If not a new 4K hard drive or SSD, it does not really matter.

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

