---
title: "Partition Woes"
date: 2008-03-09
forum: General Help
---

### Post by M4rotku on 2008-03-09
I want to dual boot Ubuntu 7.10 with my Vista system.  It seemed like it was going to be easy enough.  I went into the Vista partition editor and tried to shrink the C drive and extract 16 gigs from it for Ubuntu.  However, Vista won't give up more than 1 gig of memory.  I went on a windows forum and discovered that Vista has some of there indexes(i think that's the word) stored in a specific spot, so it limits what you can shrink.

I tried then to use Partition Magic to shrink it, but that also did not work.

My question: Do I need to create a partition in order to install Ubuntu?

---

### Post by taurus on 2008-03-09
You might want to defrag your windows a couple of times first and see if you can resize your harddrive then.

---

### Post by M4rotku on 2008-03-09
What would defragging do to my files and such?  I don't have a disk for Vista btw, the comp didn't come with one, so if it's gone, it's gone.

---

### Post by taurus on 2008-03-09
[http://en.wikipedia.org/wiki/Disk_Defragmenter_(Windows](http://en.wikipedia.org/wiki/Disk_Defragmenter_(Windows))

[http://www.geekgirls.com/windows_defrag.htm](http://www.geekgirls.com/windows_defrag.htm)

---

### Post by M4rotku on 2008-03-09
Thanks, I'll research it and then try it.

---

### Post by M4rotku on 2008-03-09
I defragmented my hard drive using the utility that came with vista and then there was 0 gigs available to shink from the C drive.  Do I really need to have a second partition to install ubuntu on?

---

### Post by M4rotku on 2008-03-09
bump

---

### Post by taurus on 2008-03-09
If you don't have a whole lot of space left on your harddrive, why not just get another one and install Ubuntu on that new second harddrive.  Then, you don't have to worry about defrag or resize the harddrive that Vista is on.

---

### Post by M4rotku on 2008-03-09
I have 154 gigs of free space on my current hard drive.  The problem is that Vista spreads itself out so that some of its nonmoveable files are at the beginning of the drive, the moveable files are in the middle of the drive and then one decent sized, unmoveable file is at the end of the drive preventing me from choping the end off and repartitioning it.  Now you can see why i'm getting frustrated and moving to Ubuntu in the first place.

When I installed Ubuntu on my other computer, I didn't have to create a partition ahead of time, can I just do that again?

Edit: grammar

---

### Post by taurus on 2008-03-09
Unless you want to install Ubuntu over your Vista, erasing Vista, you need to create an empty space for it.  Now, in the partition screen from Ubuntu LiveCD, you can tell the installer how much space you want to reserve for Ubuntu.  You can try that option to see if the installer can create any empty space for it.  Otherwise, you can either tell the installer to use the whole disk, erasing Vista, or get another harddrive and install Ubuntu on that harddrive.

I am not sure if some of those commercial defrag apps would move everything to the beginning of the harddrive.  You can have a lot at those if you wish.

---

### Post by M4rotku on 2008-03-09
I've tried 3 different defragmenters so far and none of them moved the files, I guess i'll try installing and seeing if i can reserve space for it.  Grr, I hate Vista.

Thanks for the advice.

---

### Post by forrestcupp on 2008-03-09
> **taurus said:**
> Unless you want to install Ubuntu over your Vista, erasing Vista, you need to create an empty space for it.  Now, in the partition screen from Ubuntu LiveCD, you can tell the installer how much space you want to reserve for Ubuntu.  You can try that option to see if the installer can create any empty space for it.  Otherwise, you can either tell the installer to use the whole disk, erasing Vista, or get another harddrive and install Ubuntu on that harddrive.

I am not sure if some of those commercial defrag apps would move everything to the beginning of the harddrive.  You can have a lot at those if you wish.

This is your answer.  You don't need another partitioner.  Just install from the Ubuntu LiveCD.  Part of the installation process is a partitioner and you can choose to install using the free space on your hard drive. It should detect how much free space you have and allow you to choose how much space you want for Ubuntu.  Then it will do the partitioning for you.  **You don't want to choose the option to install using the entire drive**.  

When you are done, you will have a dual boot system with Ubuntu and the Vista install that you already had.

---

### Post by M4rotku on 2008-03-09
I tried the booting partitioner, and it couldn't detect any free space.  Vista has succeeding in eating all of my hard drive.  I talked to a friend and he recommended another defrag called JkDefrag, so i'm trying that.  If anyone has succeeding in dual booting a Vista system then your advice would be greatly appreciated.  I'll keep everyone updated with the success of this defrag.

---

### Post by M4rotku on 2008-03-09
it didn't work

---

### Post by M4rotku on 2008-03-09
I'm considering trying to switch from Vista to XP and then dual booting the XP and Ubuntu.  I wouldn't mind using XP over Vista anyways.

---

