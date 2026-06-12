---
title: "How do I rearrange my partition and extend my ubuntu partition?"
date: 2018-07-24
forum: General Help
---

### Post by andraantariksa on 2018-07-24
I've a problem, I want to resize my Ubuntu partition, but I can't resize it because these 2 partition blocking me.


[IMG]https://i.stack.imgur.com/pU3aU.png[/IMG]



Do you have any idea how I should manage this? I can manage with linux partition, but I don't have any idea how I could manage the windows parititon. I'm thinking to move unallocated to the left side of windows partition and clone the recovery partition to it.

---

### Post by Dennis N on 2018-07-24
I would make an ext4 partition in the unallocated 30 gB, mount it in Ubuntu with an /etc/fstab entry at startup, and use it as a data partition, adding 30 more gB for your files.

---

### Post by oldfred on 2018-07-24
With gpt difficult to clone partition.
Partitions have both UUID & GUIDs and unique GUID is in primary partition table, partition and backup partition table. A clone may duplicate those and create major issues. 
If just copying data then it is ok as each partition then is unique.

Why ext3 or is Windows just not showing it correctly?
Better on Linux forum to use gparted screen shots. And Please attach screen shots, not post in line.
Forum in its advanced editor and paperclip icon makes it easy to upload screen shots.

Also backups should be to other devices. When I got the one Dell with Windows it wanted Dell backup, Windows backup & I did a full backup of Windows with Macrium Reflect. Several flash drives & DVDs but then able to restore system when hard drive fails, note when, not if.

---

