---
title: "Cannot mount volume"
date: 2008-07-08
forum: General Help
---

### Post by Jimbo13 on 2008-07-08
I'm trying to access a second internal hard drive (250GB IDE) that has my media files on it. My system does not have a windows OS install on it and neither does the 250GB but it was in a windows box. 


[IMG]http://img228.imageshack.us/img228/3032/screenshotgnomemountsu5.png[/IMG]

I went to terminal and tried the force and received 

[IMG]http://img178.imageshack.us/img178/8140/screenshotjimjimserverlk4.png[/IMG]

The pic says ntfs -2g I tried 1g through 5g thinking this might be a reference to the drive position I think I'm wrong.

Anyways any guidance to get at my music is greatly appreciated.

---

### Post by justleen on 2008-07-08
```
 mount -t ntfs-3g /dev/sdb1/ /media/disk -o force 
```

note the (lack of) spaces on several places.

---

### Post by sisco311 on 2008-07-08
If you have a dual boot system,  then reboot in windows and make
a clean shutdown(no hibernation).


Or try to mount the partition with the force option:
```
sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```sudo = you need root privileges to mount a disk
ntfs-3g = the name of the driver (in hardy you can use ntfs)
/dev/sdb1 = the name of the partition (like d: in windows)
/media/disk = the mount point(open your file browser and check if exist.
If not, run
```
sudo mkdir /media/disk
```to create it)

---

### Post by Jimbo13 on 2008-07-08
All fixed, sudo mkdir /media/disk did the trick.

Thanks.

---

### Post by justleen on 2008-07-08
please mark it as solved then :)

---

