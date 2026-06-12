---
title: "Missing EXT3 Partitions after Cold Shutdown"
date: 2006-10-12
forum: General Help
---

### Post by scott_ttocs46 on 2006-10-12
Hi all,
    I have two extra drives and two missing EXT3 patitions that have irreplacable data on them. Any ideas how to recover the data?

I think this was caused by a power failure. 

Also, the error says something about an "unsupported inode size" (??)

Thanks,
Scott

---

### Post by scott_ttocs46 on 2006-10-12
[4294683.362000] EXT3-fs: unsupported inode size: 0

---

### Post by scott_ttocs46 on 2006-10-12
Can use one drive now. I booted into the older kernel.

---

### Post by scott_ttocs46 on 2006-10-12
Fsck exits with signal 8 on /dev/hdb1 (the drive that still is not working). What does that mean?

---

### Post by scott_ttocs46 on 2006-11-09
*REALLY *DISAPPOINTED IT TOOK THIS LONG!
[COLOR="YellowGreen"]**BUT I HAVE A SOLUTION!!!!!!!!**[/COLOR]

Command is:

[COLOR="Red"]**sudo dd if=/dev/zero of=/dev/hdb1 bs=4 count=1 seek=275**[/COLOR]

Found it on:

[http://lkml.org/lkml/1998/12/12/134](http://lkml.org/lkml/1998/12/12/134)

It also has a useful patch for the kernel. I am not that experienced with coding in linux. A more experienced user could make a *very *useful update for the community.

---

