---
title: "Help please"
date: 2007-03-13
forum: General Help
---

### Post by Scubastev013 on 2007-03-13
Hey everyone. I have a few questions for you guys. I will be switching to Mac to college, and in the meantime, I need something other than windows. Its driving me nuts.

1. I am trying to install ubuntu to a seagate external hard drive (~205GB USB). Everytime I go to install it, the install process hangs when I try to have it automatically divy up the hard drive to install linux in a separate partition (I want to give it ~80 GB) I have other stuff on the hard drive I want to keep. How do I do it? haha. I've tried a few other things, but none seemed to work, and I don't want to give the whole hard drive to linux (as I need somewhere to back my stuff up to)


help!

---

### Post by peabody on 2007-03-13
Hate to say, but it might be safer to use something like Partition Magic in Windows, or the Gparted cd to split the drive ahead of time.  Once the space is set aside I imagine the install should work.

---

### Post by Scubastev013 on 2007-03-13
Would this problem have anything to do with the filesystem? Its FAT32. Should I change it to NTFS or another one?

---

### Post by peabody on 2007-03-13
Nah, I figure Fat32 would in your favor actually.  NTFS is more typically the problem filesystem under Linux.  If shrinkin' the partition during the install doesn't work--it doesn't work, simple as that.  I don't have a URL, but I heard there's a free partitioning CD known as the Gparted boot cd.  Google'll probably turn it up.

If you set the space aside ahead of time the install should probably work.

---

### Post by Scubastev013 on 2007-03-14
Gparted and Partition magic 8.0 couldn't touch my disk.  I don't know why.  Actually, Gparted didn't even boot.  What should I do?

---

### Post by peabody on 2007-03-14
The fact that it's an external drive may have something to do with it.  What type of port (I'm assuming USB 2.0 is the likely port).  Bummer on gparted not even booting.  I'll try googling for any problem related to seagate externals and Linux.

---

### Post by kolinab on 2007-03-14
What errors did you encounter when the GParted CD didn't boot? Are you sure you wrote the .iso to the CD properly? (first things first :))

---

### Post by Scubastev013 on 2007-03-14
I think my CD burner is malfunctioning.  That sucks.  I'll get it done on the other burner when I get the chance.  I'll let you know how it goes.  In the meantime, what file system should I set the Ubuntu partition for?  NTFS?  FAT32? FAT?


Thanks

---

### Post by peabody on 2007-03-14
You should just leave the space unpartition.  By default, the preferred filesystem for Ubuntu is ext3.  You should just let the install go for that.

---

