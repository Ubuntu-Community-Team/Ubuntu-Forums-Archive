---
title: "repartitioning"
date: 2007-03-22
forum: General Help
---

### Post by dracomordag on 2007-03-22
alright, in preparing for the upgrade to feisty, and following general consensus on these boards, i'd like to create a seperate /home partition.

i'm following this guide: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

however, my initial setup is a little different. due to my HD size limitations, the largest amount of free space i have is currently in my NTFS partition. I'd like to resize the NTFS to as small as possible, create a small / directory following, then have a large amount of space for my /home directory (and obviously a tiny swap at the end)

so basically i have the following:
[NTFS(30 used out of 50 GB)][EXT3(20 used out of 30 GB)][swap(1 GB)]

and i'd like it to become

[NTFS(30 out of 30 GB)][EXT3 "/" (as small as possible)][EXT3 "/home"(everything left)][swap]


how can i do this?

---

### Post by mikewhatever on 2007-03-22
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Gparted live cd is a newer version of the partitioner on Ubuntu live cd. You can use any of the two the same way you must have used it the last time you got Ubuntu installed. Sorry if I don't quite understand the difficulty.

---

### Post by dracomordag on 2007-03-22
using gparted as it stands now, this is all i can get to:

[NTFS(30 out of 30)][Ext3(0 out of 20)][Ext3(20 out of 30)][swap]

it needs to be

[NTFS(30 out of 30)][Ext3(0 out of 8 )][Ext3(20 out of 42)][swap]


i guess i'll just have to go out and buy yet another external HD and back everything up to that, then wipe everything and start from scratch.

---

### Post by zvacet on 2007-03-22
Download Gparted live CD as Mikewhatever told you.Delete ext(0 out of 20),and click on ext(20 out of 30) and resize.

---

### Post by dracomordag on 2007-03-22
it doesnt let me do that... was that not clear from the very first post? I've had gparted the entire time, but when you have a blank partition followed by a partition with data, it doesnt let you move the data into the empty space.

my current plan is to create
[NTFS(30 out of 30)][Ext3(0 out of 20)][Ext3(20 out of 30)][swap]

delete the two EXT3s (having moved that 20GB data onto an external HD), then create the new ones, sized as i would like them, and move the data back on.

---

### Post by kleam on 2007-05-04
OHKAY SO, When I went from windows xp (NTFS) to Ubuntu I used a friendly program called Partition Magic. It is a very nifty program that works with Fat32 and NTFS file systems and partitionings. I haven't worked with them on Linux yet. but i will be doing a project tonight that closly respembles yours

I was thinking, if you can, log onto the NTFS partition and run Partition Magic. In there you can resize the partition and set the free space up for your new /home.

If you don't actually have a OS installed on that NTFS partition then you can download the ISO for [PARTITION MAGIC]("http://en.wikipedia.org/wiki/Partition_Magic") and maybe run it with Wine 0.9.6

When I get home I can see if i can make a torrent for you to get Partition Magic or you could look it up.

I'm sorry if I actually don't make any sense. I donh't have much experience with Ubuntu or Linux, but i hope i helped


-Kleam

---

