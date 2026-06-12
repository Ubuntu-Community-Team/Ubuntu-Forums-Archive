---
title: "Raid 1 -advice/help please"
date: 2018-03-27
forum: General Help
---

### Post by dee119 on 2018-03-27
:) Hi and thanks in advance for anyone's input.

Firstly I hope this is in the correct part of the forum, so please excuse if not.

I am trying set up my system with Raid 1 in 16.04 - although I am no expert or indeed
have much knowledge on the subject, so please bear with me.

I have two (2) Hdd's of 500Gb each, with partitions on both drives.
Have downloaded #mdadm and installed it.

From the command line, when I go too create md0 which most guides and instructions 
recommend to use, I get the following output:- 

'/dev/ sda  /dev/sdb  is busy  (this is shortened version of the output)

My questions are as follows:-
1) Do both Hdd's have to be empty to setup raid
2) Have I to use a 'Live' CD version to attempt the raid
3) There is raid in the Bios - do I have to do anything there - most say do raid via software

If any of the above makes sense to anyone and they could guide me in the right direction,
then it would be much appreciated.

As I said,  I am no expert on Linux, but can do a few things at the command line which
hopefully may be of some use.

Thank you for taking the time to look at my problem,  and thank your for any input forth coming.

Regards - Dee


.

---

### Post by TheFu on 2018-03-27
No.  Both HDDs don't have to be empty, but you need to specify which partition(s) should be used.  Actually, I prefer to have at least 1 partition on my RAID1 disks so I don't get confused and think a disk doesn't have any data, which is what a disk with RAID directly on the disk, not on partitions can look like.

Be very careful specifying devices.  Linux might do what you ask, not necessary what you intend.
/dev/sda - is the entire disk drive
/dev/sda1 - is the first primary partition - assuming GPT or MBR partition tables.

Today, I can't think of a reason to use MBR for anything on Linux.  GPT is easier and better for a number of reasons.

If the disks are locked, in-use, they cannot be modified. If that is the situation, might be useful to boot from flash media to do any partition work that you need.   howtoforge has a RAID guide that should be helpful.  It explains with real examples.  It might be helpful to practice using a virtual machine with relatively tiny partitions too.

If you see issues, it is best to show the EXACT command used  and all the relevant output. Please use code tags.  That is most helpful, rather than trying to explain.  It also reduces the chance for a misunderstanding on either side from causing harm to your data.

BTW, whenever doing partitioning or disk stuff like RAID setup, it really is important to have all that data backed up somewhere else. A tiny mistake can easily wipe the disk ... like using /dev/sda when you should use /dev/sdaX. That could be very bad for the data.

---

### Post by rsteinmetz70112 on 2018-03-27
I'm a little unclear exactly where you are and what you're trying to do.
If this is a new system and you want it on a raid array you will need to set up the raid array before you install the Ubunt

To set up an array first start the computer in Ubuntu with neither drive mounted.
You can use your existing system, a DVD or a USB drive.
 
Then using fdisk create a partition on each drive. 
Using fdisk define each partition as linux raid.

Using mdadm create an array with two disks.

You probably want to make sure /etc/mdadm.conf in your root partition.

From there you can generally treat the array /dev/mdX as a regular block device.

---

