---
title: "Bad Block?"
date: 2008-02-23
forum: General Help
---

### Post by Locutus_of_Borg on 2008-02-23
I just installed 7.10 the other day and all was fine until I extended the partition to include about 75 GB of free space (previously occupied by 7.04) now fsck spits out a several lines saying "exception emask" then lists one bad block (resulting in a short read during inode scan or something similar) and then tells me I have 0.9% non-contiguous files.

Is there a reason and/or solution to this?  I had a similar problem with 7.04 and after countless fsck runs with varying options was never able to solve this.  At least it's only one block (had been about a dozen with feisty). I don't really want to re-install again, and would that even fix this since this install is only about 2-3 days old?


Thank you.

---

### Post by Herman on 2008-02-23
Having bad blocks in a hard disk is perfectly normal, all hard disks have a few bad blocks, even when they are brand new.
In normal usage, a few more blocks may fail as time goes on.
However, hard disk manufacturers provide some extra space in the hard disk where there are some spare blocks that can be quietly swapped electronically, for any bad blocks in the rest of the hard disk so the operating system and therefore the new isn't aware of any bad blocks existing.
When you do become aware that there are some bad blocks, it is usually a sign that the hard disk is on its way out, because that means it has already allocated it's entire reserved area of spare blocks and has no more good blocks left to swap for any new bad ones.

If you have an ext3 file system, here is a command that should help your file system cope with bad blocks for a while longer, ```
sudo e2fsck -c -c -k -v /dev/hda2
``` Where: /dev/hda2 is the right partition number, check by looking with Gnome Partition Editor or with the 'sudo fdisk -lu' command.
Where: You run any file system check commands on an unmounted file system, (from a live CD is a good idea, or from a different operating system on the hard disk, as long as you unmount the one to be checked first).
That command is supposed to get the file system to record where the bad blocks are and so it will re-arrange itself so it won't use that spot on the hard disk.

It may still be okay to continue using your hard disk even when there may be a few bad blocks, it might still last a while,just make sure you have all your data backed up, which you are supposed to do at all times anyway.
It would be better to get a new hard disk for your operating systems and keep the one with the bad blocks but give it an easier job as a data disk. It might still last a while in a less demanding role and you can keep an eye on it. It depends on your budget. For some people it is not worth wasting time with a dodgy hard disk at all, particularly if the data is valuable. Hard disks are relatively cheap these days.

Regards, Herman :)

---

### Post by Locutus_of_Borg on 2008-02-23
Thank you for the response.  I was worried about the hard drive failing as my laptop is about 1.5 years old now.  I will try that command from a live disk. I have run numerous other similar commands, but I cannot remember exactly if I have attempted that particular set of options. It seems though that the bad block is located towards the end of my drive as my first partition checks out clean, and my second had as well up until I extended it to the last 70 or so gigabytes.  I don't suppose though it is possible to confine my OS to the first half, up until that block, and use the remainder as a storage partition without running into more problems, is there?

---

### Post by Herman on 2008-02-23
Here's what the e2fsck options in that command are for (quoted from the e2fsck manual)
> -k     When  combined  with  the  -c  option, any existing bad blocks in the bad blocks list are preserved, and any new bad blocks found by running badblocks(8) will be added to the existing bad blocks list.> -c     This option causes e2fsck to use badblocks(8) program to do a read-only scan of the device in order to find any bad blocks.  If any bad blocks are found, they are added to the  bad  block
              inode to prevent them from being allocated to a file or directory.  If this option is specified twice, then the bad block scan will be done using a non-destructive read-write test. > -v     Verbose mode.1.5 years is not very old for a hard disk drive, but I suppose there are a lot of factors to take into consideration, a lot would depend on how much the machine is used and what it's used for, and luck probably plays a role too. 

Another command you might find interesting would be,
```
sudo badblocks -n -v /dev/hda2
```Where: /dev/hda2 is the right partition number, check by looking with Gnome Partition Editor or with the 'sudo fdisk -lu' command.
Warning: That command might take a long time to run, and may not produce any output or show any progress bar.
If you do get output that's when it is finding problems, if no output is shown then your hard disk is fine. When the command is finished your terminal command prompt will appear again.

You may also be interested in [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").
Smartmontools can be installed in Ubuntu with,
```
sudo apt-get install smartmontools
```Regards, Herman :)

---

### Post by Locutus_of_Borg on 2008-02-23
Thank you very much for the replies again.  I will try those tonight when I have more time to spare.  I don't know if this would be a contributing factor to the hard dive possibly failing, but I have been partitioning and repartitioning a lot lately, plus this laptop is running probably 90% of the day (either standby mode or regular use).  I've been planning on upgrading this computer for a while now anyway, at least.

---

### Post by Herman on 2008-02-23
> I don't suppose though it is possible to confine my OS to the first half, up until that block, and use the remainder as a storage partition without running into more problems, is there? That might help, but bad blocks can appear at random on any place in the hard disk. It would be impossible to predict where the next one will turn up.

---

### Post by Herman on 2008-02-23
> I don't know if this would be a contributing factor to the hard dive possibly failing, but I have been partitioning and repartitioning a lot lately, plus this laptop is running probably 90% of the day (either standby mode or regular use). I've been planning on upgrading this computer for a while now anyway, at least. I don't know, but I tend to leave my computers running quite a lot of the time too, and I also do a lot of partitioning and repartitioning. I have a website about how to install with the 'Alternate' CD which requires a lot of test installs to update the website when each new Ubuntu version is released, and I like installing and deleting operating systems just for fun sometimes too. :)

I have only had one old second hand hard disk fail on me so far, it was quite an old 6.0 GB laptop hard drive. That one appears to have suffered a bearing failure, judging from the oily stain under a sticker below where the spindle would be.

The rest of my hard drives all seem to be fine, so I don't think the number of times they have operating systems installed in then and deleted again seems to be a significant problem. :)

I read this is a page I was studying for information about hard disks,
> Studies have shown that lowering disk temperatures by as little as 5°C significantly reduces failure rates, though this is less of an issue for the latest generation of fluid-drive bearing drives. 
One of the simplest and least expensive steps you can take to ensure disk reliability is to add a cooling fan that blows cooling air directly onto or past the system's disks. Almost all laptop owners, (myself incuded), run their laptop at some time or another on a soft surface like a bed which could restrict the flow of cool air into the vent under the laptop.
Another thing we all do (incudling myself) with our laptops is move them around while they are running and the hard drive is still spinning. We need to be carefull bump to laptop when we do that and shock the hard drive.
Yet another problem with laptops is when we're running on the battery and the battery runs out, but I don't think that would cause bad blocks, maybe only file system corruption that should be fixable with a regular file system check.
Even if you didn't do any of the above things that most of us to with our laptops, you could still have a hard drive that was made on a bad day at the hard drive factory somewhere, when a machine ran a little out of adjustment, and your hard drive is almost perfect but ... of course those things never happen, and are caught by 'quality control', but what if a batch of hard platters are 'borderline'?
So a lot probably depends on luck as well.

Regards, Herman :)

---

### Post by Locutus_of_Borg on 2008-02-27
Well, I am still left with bad blocks after all of this, smartmontools though says my hard drive is healthy.  badblocks gave me an output of about 25 blocks it suspects to be bad.  Would it be wise to use debugfs to free all of those blocks from their respective inodes and mark them all as allocated so as they are not used anymore? Or is this a bad idea?
Thanks.

---

### Post by Herman on 2008-02-29
:) Have you been doing some reading on this subject? I have, I found this excellent link in another Ubuntu Web Forums thread, submitted The Mekon in post # 6 of thread: [how to locate and map out bad sectors]("http://ubuntuforums.org/showthread.php?t=309822").
Here is the link: [Disk Maintenance under Linux (Disk Recovery)]("http://www.linuxjournal.com/article/0193") by David A Bandel in The Linux Journal.

I think the command you already used would have done the same thing already with a lot less work though. I'm not really sure, I have only had one hard disk fail on me and that was quite some time ago. I wish now that I had kept better records of which commands I used and how long before I had to run more commands to keep the disc working a bit longer. In my case, the disc kept developing badblocks and more badblocks at an accelerating rate until it failed completely.
Yours might (probably) be a completely different situation, and it will be interesting to see what happens.
I would definitely be making frequent backups.

I'm not a file system or hard disk expert, I'm just someone else who's also trying to learn stuff, so take my opinions here with a grain of salt.  I think bad blocks are areas of the hard disk where the ability of the hard disk material to hold a magnetic field is relatively weaker than whatever program you are using to detect the bad sectors thinks it should be. Maybe that;s why the badblocks program is telling you you have badblocks but your hard disk itself (the information you're reading with smartrmontools), isn't considering them bad. (Maybe the badblocks program is set to pick out blocks that are only a little bit bad). I'm just guessing about that. Maybe someone will come along and add a better informed comment.
I would have to wait for some of my hard disks to fail or try to get failing hard disks from somewhere and try some experiments with them to learn more.

Regards, Herman :)

---

### Post by Locutus_of_Borg on 2008-02-29
The other night I read a lot more about this issue and came across that Linux Journal article which is where I learned of the debugfs utility.  I have not tried to implement it yet though, since I can now pass a fsck scan and boot properly.  I also resized my root partition and am using the potentially bad sectors of my disk as /home...which may or may not be wise on my part, but I have made backups of all important things anyway, and the worst I can lose at this point is pirated anime/star trek episodes :)

---

