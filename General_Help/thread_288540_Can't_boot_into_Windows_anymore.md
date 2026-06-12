---
title: "Can't boot into Windows anymore"
date: 2006-10-30
forum: General Help
---

### Post by Ralle on 2006-10-30
hello guys.
Before I was using the dapper and could boot into windows and ubuntu but now I got edgy. It says that my windows partition (ntfs) is an unknown type which is weird. here's part of my menu.lst
```
title		Microsoft Windows
rootnoverify		(hd0,2)
savedefault
makeactive
chainloader	+1

```
I tried both root and rootnoverify.

---

### Post by cptnapalm on 2006-10-30
That's very strange.  My little xp partition works fine... not a problem in the least.

Ack, I forgot mine is a fat32 partition... :(

Ok, I do *not* know if this will help you, but there is a package called ntfsprogs which contains utilities to attempt to repair an NTFS partition.

Backup backup backup!

Any and all stuff which you deem important on that partition, back it up before doing anything with it.

---

### Post by Ralle on 2006-10-30
well that ntfsprogs is weird. I can't really find out how to mount a ntfs partition with it. And I doubt it works..
But I need it to work. I have some schoolwork I can't access.

---

### Post by Jimmy_r on 2006-10-30
Edit: if you have a scsi or sata hard drive, replace hda3 with sda3

What happens if you just do a
```
sudo mount /dev/hda3 /mnt
```
then 
```
gksudo nautilus
```
and navigate to /mnt
if your windows partition is there, backup the things you need.
then close nautilus, do a 
```
sudo umount /dev/hda3
```
and then 
```
sudo ntfsfix /dev/hda3
```

---

