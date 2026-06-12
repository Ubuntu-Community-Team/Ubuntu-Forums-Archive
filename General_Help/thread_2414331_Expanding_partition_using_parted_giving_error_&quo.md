---
title: "Expanding partition using parted giving error &quot;Unable to satisfy all constraints&quot;"
date: 2019-03-08
forum: General Help
---

### Post by schleepy on 2019-03-08
Hey there.


So  I have this hardware raid array that consists of three 8TB drives, I  recently added the third one and expanded the raid so now I got 16TB  usable on that array.


The  next step is resizing the partition with parted but simply using the  command resizepart 1 100% is giving me "Unable to satisfy all  constraints"


```
GNU Parted 3.2
Using /dev/sdb
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print free
```
I notice this error when printing free space but I choose to ignore it.
```
Warning: Not all of the space available to /dev/sdb appears to be used, you can
fix the GPT to use all of the space (an extra 15623784448 blocks) or continue
with the current setting?
Fix/Ignore? Ignore
Model: Adaptec ZArray (scsi)
Disk /dev/sdb: 15999GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End      Size    File system  Name  Flags
        0.00GB  0.00GB   0.00GB  Free Space
 1      0.00GB  7999GB   7999GB  ext4
        7999GB  15999GB  7999GB  Free Space
```
Running the resize
```
(parted) resizepart
Partition number? 1
End? [7999376MB]? 100%
Gives me this:
Error: Unable to satisfy all constraints on the partition
```.


The  partition works fine, it mounts and the data is accessible. My question  is, do I allow parted to fix the GPT to use all of the space? Could  that fix my problems or is there something else at play?

---

### Post by schleepy on 2019-03-09
Anyone?

---

