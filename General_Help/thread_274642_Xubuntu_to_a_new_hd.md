---
title: "Xubuntu to a new hd"
date: 2006-10-10
forum: General Help
---

### Post by cd-r80 on 2006-10-10
How it is easiest to move Win/Dapper to a new bigger hd? Clone & resize partitions. Or just tar/untar or copy all & copy mbr/Grub? I have Win/FAT32 & Reiserfs. Every partition need to grow... ReiserFS risks when  cloning. I have made cloning with Ghost/ ext2. But I want to stay with ReiserFS.

---

### Post by Rui Pais on 2006-10-10
the simpler should be duplicate the old HD to the new with dd command (from a liveCD) and then use gparted to adjust sizes of partitions on the new hd to the desired ones. dd will copy mbr so even grub will work.

---

### Post by cd-r80 on 2006-10-10
If I Do the dd & and then resize? Does it not destroy data if I have data on many partitions? When the first is extended over the second etc...

---

### Post by Rui Pais on 2006-10-11
hi,
well the idea is to resize and move your last partition to the end of the disc, then go on with the other before from the end of HD to the beginning.

Now that i'm thinking when i done that (2~3 years), if i remember well, last ones didn't move, probably no space enough, and i had do redo the partitons by hand with gparted and then **cp -a** from the old ones. At the time i have only ext3, that resizes and moves well and safely. Don't know if other filesystems do the same or safety as ext3...
All process taked a long time, cause first dd replicate anything, even empty space, and then the resizes/moves take another long times. A faster way to do it would be copy MBR with:
```
sudo dd if=/dev/hda of=/dev/hdb bs=512 count=1
```
assuming that /hda is your old drive and hdb the new one,

then use gparted to make the partitions with the same scheme (primary, extended and logical in the same other but bigger as desired) and then mount one by one and copy with:
```
sudo cp -a /media/hda1/* /media/hdb/
```
and so one... (the important part is the -a flag)
then move hda or change master/slave jumpers so hda became hdb and hdb hda and reboot :)

Of course that sounds a little more complicated but it's very simple and faster then dd.

hope that clarifies a little.

---

### Post by cd-r80 on 2006-10-11
Ok This way looks clear. Create and copy partition one by one to a same order. Gparted makes it all I think.

---

