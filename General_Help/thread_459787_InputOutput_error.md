---
title: "Input/Output error"
date: 2007-05-31
forum: General Help
---

### Post by auditory on 2007-05-31
All of sudden, i encountered "Input/Ouput error"
for most of basic commands like whoami, cat, mkdir an so forth

even I cannot do 'fsck'

I guess my hdd got some error.

how can i check or fix it?

---

### Post by handband2 on 2007-06-01
It is a drive formated ext2 or ext3 check out this post:  [[COLOR="Red"]http://www.eukhost.com/forums/showthread.php?t=979[/COLOR]]("http://www.eukhost.com/forums/showthread.php?t=979")

If it is a external drive with fat32 try this:
```
$ sudo fsck -t vfat -a /dev/YourDevice  (example:  /dev/sdb2)

$ sudo rm -Rvf /media/NameOfExternalDevice/BadFileOrFolder
```

---

