---
title: "RAID Failure On Ubuntu 14.04"
date: 2015-01-06
forum: General Help
---

### Post by ice29212 on 2015-01-06
[TABLE]
[TR]
[TD][/TD]
[TD]Recently my RAID 0 partition has stopped working. Its a "fake RAID" using dmraid.
When I run the command:
```
~# dmraid -s
ERROR: sil: wrong # of devices in RAID set "sil_bjaccdaaeibd" [1/2] on /dev/sdc
ERROR: removing inconsistent RAID set "sil_bjaccdaaeibd"
ERROR: no RAID set found
no raid sets
```

Not really not sure what this means. Any ideas?

Output of lsblk

```
:~# lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 298.1G  0 disk 
&#9500;&#9472;sda1   8:1    0 290.1G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0     8G  0 part [SWAP]
sdc      8:32   0 465.8G  0 disk 
&#9492;&#9472;sdc1   8:33   0 465.8G  0 part 
sr0     11:0    1  1024M  0 rom  
sr1     11:1    1  1024M  0 rom  
```

Any Ideas on this? Am I able to rebuild or rescan my disks?
[/TD]
[/TR]
[/TABLE]

---

### Post by ice29212 on 2015-01-06
Anyone? Am I dead in the water here?

---

