---
title: "HELP - Mounting NTFS partitions with LIVE CD"
date: 2007-02-17
forum: General Help
---

### Post by jbtito03 on 2007-02-17
Hi guys...

I need some help. i am sitting on my friends laptop and his win xp chrashed and i am trying to mount the disk with the ubuntu live CD. Now, as always, ubuntu does not want to mount them. 

How can i force it to mount them. And.... it is the only thing that is possible because we need the laptop in about 2 hours ready to play music on a party as my friend is a DJ.

Please someone to help on this one.


Cheers

JB

---

### Post by taurus on 2007-02-17
Assuming it is /dev/hda1, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs /dev/hda1 /media/windows -o nls=utf8,umask=0222
df -h
```

---

### Post by karcin on 2007-03-02
I had the same problem, 
and this way I solved it.
Thanks taurus.

---

### Post by kooldino on 2007-11-14
My buddy has this issue...I'll see if this works for him and report back.

---

