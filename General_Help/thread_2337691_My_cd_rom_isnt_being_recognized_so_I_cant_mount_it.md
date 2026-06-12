---
title: "My cd rom isnt being recognized so I cant mount it"
date: 2016-09-20
forum: General Help
---

### Post by jewpacabra on 2016-09-20
I have been trying to mount my cd rom and have tried multiple things. None have worked. 
This is is what I get 
```

$ sudo lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 465.8G  0 disk 
&#9500;&#9472;sda1   8:1    0 449.8G  0 part /
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0    16G  0 part [SWAP]
sdb      8:16   0 931.5G  0 disk 
&#9492;&#9472;sdb1   8:17   0 931.5G  0 part /media/administrator/BF0A-8DC1
sdc      8:32   0   1.8T  0 disk 
&#9500;&#9472;sdc1   8:33   0   200M  0 part 
&#9492;&#9472;sdc2   8:34   0   1.8T  0 part /media/administrator/TOSHIBA EXT

```

---

### Post by mcduck on 2016-09-21
Just to be sure, is this with a valid data CD inserted in the drive? The drive itself isn't a block device and doesn't contain a filesystem so it wouldn't appear in lsblk.

---

