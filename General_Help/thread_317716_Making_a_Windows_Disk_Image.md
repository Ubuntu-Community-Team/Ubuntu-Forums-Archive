---
title: "Making a Windows Disk Image"
date: 2006-12-12
forum: General Help
---

### Post by hebetude on 2006-12-12
I wish to temporarily (1 week or so) remove everything on my 20gig Windows Partition, leaving only my Ubuntu partition.  So I'd like to make a backup of the drive that I can use to rebuild the partition later.  

So my question is what is a safe way to go about this?  If this is high risk, I won't even bother trying.  I'd just like the disk space for a week.

---

### Post by yer on 2006-12-12
I know you probably want to hear an open source solution, but IMO the best way to safely and reliably back up a partition (and compress it, too) is norton ghost. Best of all, Symantec included EXT filesystem support! You can ghost your windows drive and save the image file on your nix drive to restore it later. Even better you dont have to install ghost, you can run it off the CD (its bootable). I have worked as a computer tech since 2001. Out of all the disk backup software I've tried (maybe twenty or so) Ghost is the best. FYI, there is a ISO CD image floating around the internets called Techiez Tool kit. It has EVERYTHING on it, including ver. 7 and 8 of Norton Ghost. Also some utilites to recover corrupted partitions, bad blocks, ect. It also has all the drive manufacturer's tools for hard drive repair. I carry 3 copys of it wherever I go. Oh yeah, its got memtest86+ on it too. Man, that little utility has saved my but a thousand times.

---

### Post by scxtt on 2006-12-12
any reason partimage {from the ubuntu repos} wouldn't work? ... just pop in a live cd, **aptitude install partimage**, save the partition backup somewhere and reload it whenever you want ... i did that to ubuntu when i was trying out suse 10.1 (on my actual hardware) ...

---

### Post by yer on 2006-12-12
Like I said, IMO (in my opinion, (opinions are like assholes, everyone has one, and they all stink)) ghost is the best. I espesially like the options for including the MBR in the backup image, makes restoration alot easier. nothing like firing up your freshly restored image and finding it unbootable. Also, I had a bad experiance with partimage, I used it to resize a NTFS drive and it became unmoutable. Luckally, I was able to ghost that partition to a image on another drive, repartition the first drive, and ghost it back without loosing any data (it was a dual boot redhat 9 win2000 box).

---

### Post by yer on 2006-12-12
OoOps. I mean Gparted. not partimage. I will look into partimage.

---

### Post by hebetude on 2006-12-12
Thanks for the info, I was hesitant to use the standard Partition tool for the exact reason yer mentioned.  I've used Partition Magic many times on this laptop, however it now errors at any attempt to read the partition.  So, I didn't think it was safe using any tool to do it.

---

### Post by aysiu on 2006-12-12
If you are having weird disk errors, probably the best way to back up the partition is using *dd_rescue*:
[http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/](http://ubuntu.wordpress.com/2006/01/21/rescue-data-from-failing-partition/)

---

### Post by yer on 2006-12-12
> **hebetude said:**
> Thanks for the info, I was hesitant to use the standard Partition tool for the exact reason yer mentioned.  I've used Partition Magic many times on this laptop, however it now errors at any attempt to read the partition.  So, I didn't think it was safe using any tool to do it.

NOOO don't use partition mangler! It mangles your data! lol. I have had alot of trouble with partition magic destroying data. several times I had customers come into the shop that had used it and then couldnt use their disk. Most of the time i was able to recover it with one of the utities on the Techiez disc.

---

