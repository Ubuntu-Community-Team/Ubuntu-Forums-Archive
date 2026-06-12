---
title: "GParted crashed when shrinking partition"
date: 2017-08-14
forum: General Help
---

### Post by eragonsvk on 2017-08-14
Hello, 
I was shrinking my /dev/sda2 by 600000MB, everything was running ok and then, GParted crashed, I was watching log and it crashed when it was "Updating Inode References XXX---------" , (I dont know how much of "-"  were there). I tried to boot it, but it didn't work, of course. 
Any help? First of all I need to recover files

---

### Post by VMC on 2017-08-14
I'm guessing sda2 was an active linux os. Too late now, but I've always had trouble resizing an active partition using *gparted*. It takes me hours to accomplish.  What you could have done was use *fsarchiver* to save the partition then delete the partition in question and size it to what you want. Then restore *fsarchiver* to the new partition.It would go much faster. 
Other than that , *TestDisk* might recover some files.

---

### Post by gedakc on 2017-08-16
Ideally you have a backup which you can use to restore your files.

If not, you might look into [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") which will scan the disk surface looking for file types it recognizes.  Note that this is a time intensive process and does not restore file names.

---

