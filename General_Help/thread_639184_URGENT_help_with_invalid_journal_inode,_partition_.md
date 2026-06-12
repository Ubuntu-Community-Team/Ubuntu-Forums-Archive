---
title: "URGENT help with invalid journal inode, partition recovery"
date: 2007-12-12
forum: General Help
---

### Post by phineaus on 2007-12-12
So I have posted a couple times in the evolution of this problem, but I recently had a moment of clarity (if that is possible), and I need help URGENTLY with a very specific dilemma.  The following gives some current information about my drive and partitions, and I cannot mount /dev/hda5, which corresponds to my main linux partition (43 gb) that I am trying to recover.  

[PHP]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x783d8f59

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1612    12948358+   7  HPFS/NTFS
/dev/hda2            1613        7297    45664731    f  W95 Ext'd (LBA)
/dev/hda5            1613        7220    45046197   83  Linux
/dev/hda6            7221        7297      618471   82  Linux swap / Solaris

Disk /dev/hdd: 8455 MB, 8455200768 bytes
255 heads, 63 sectors/track, 1027 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1f7be346

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1        1026     8241313+   7  HPFS/NTFS
ubuntu@ubuntu:~$ dmesg | tail
[31868.449462] ADDRCONF(NETDEV_UP): eth0: link is not ready
[31879.307848] ath0: no IPv6 routers present
[32480.678118] cdrom: hdc: mrw address space DMA selected
[33283.813765] cdrom: hdc: mrw address space DMA selected
[33462.706405] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[33462.706419] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=25905122, sector=25905122
[33462.706430] ide: failed opcode was: unknown
[33462.706440] end_request: I/O error, dev hda, sector 25905122
[33462.706958] EXT3-fs error (device hda5): ext3_get_inode_loc: unable to read inode block - inode=8, block=1027
[33462.707771] EXT3-fs: invalid journal inode.
ubuntu@ubuntu:~$ [/PHP]

As can be seen in the last two lines of this code, I have a problem with an invalid journal inode when trying to mount this linux partition.  This makes sense because the following is what happens as well with fsck, tune2fs, and debugfs:

[PHP]ubuntu@ubuntu:~$ sudo e2fsck /dev/hda5 -v -y -b 32768
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Attempt to read block from filesystem resulted in short read while checking ext3 journal for /dev/hda5

ubuntu@ubuntu:~$ sudo tune2fs -f -O ^has_journal /dev/hda5
tune2fs 1.40.2 (12-Jul-2007)
The needs_recovery flag is set. Please run e2fsck before clearing
the has_journal flag.

ubuntu@ubuntu:~$ sudo debugfs /dev/hda5
debugfs 1.40.2 (12-Jul-2007)
/dev/hda5: Can't read an inode bitmap while reading inode bitmap[/PHP]

If extremely interested and you have not seen my posts in the last week or two here are the links (from newest to oldest) that all started with me getting an error 18 from Grub, and later mutated to an error 17:

[http://ubuntuforums.org/showthread.php?t=637404](http://ubuntuforums.org/showthread.php?t=637404)

[http://ubuntuforums.org/showthread.php?t=629815](http://ubuntuforums.org/showthread.php?t=629815)

[http://ubuntuforums.org/showthread.php?t=625568](http://ubuntuforums.org/showthread.php?t=625568)

*a warning...if you are going to refer to something in a previous post, please take the time to read it all and understand the context.  In my experience, the more information about a problem the better for the level of user that might be able to help me with this problem, but the main problem at hand throughout my posts has been journaling problems with an ext3 linux partition.  

I was happily using a fresh install of Gutsy for about a month on this desktop, and had not altered my installation in any way prior to the regular shutdown that produced this problem (Grub will not load with error 17).  

Is there anyone in this wonderfully helpful world of ubuntuforums that might be able to shed some light on making a replacement journal, removing the journal, or something else that might at least permit me to read and copy from this partition from the liveCD, if not boot from it again?

pps.  I like the code boxes that ppl use in their posts, but not sure how to do that.  The php button was the only thing that I found in the editor, but not sure what that means...i forgot html a decade ago.

---

### Post by gaten on 2007-12-13
The only thing that I could suggest would be some disk recovery tools, so here they are:


MHDD (best one out there, IMHO): [http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)

TestDisk: [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

This page also has a bunch of hd stuff: [http://www.myharddrivedied.com/presentations_software.html](http://www.myharddrivedied.com/presentations_software.html)

Sorry if you've gotten this run around before, but this is the best I can offer.

You also might want to try and create an image of your hdd, and try to extract the info/repair the image.

---

### Post by phineaus on 2007-12-13
Thanks for the comprehensive list of utilities.  I have used testdisk on this particular drive, but it only makes alterations to the partition table as far as I could get.  MHDD sounds like its worth a shot, but it doesnt mention anything specific to linux partitions and appears to be an ms-dos program.  When I boot the liveCD for Gutsy, I am able to access the windows partition on that disk (19gb or something), but not the linux partition (43 gb), which is why I went down the track to see if it was a journaling issue.  

That said, I would love to make a disk image of the partition (probably using dd), but I do not have another space as big as that 43gb anywhere on the computer.  These suggestions remind me of a very bad disc crash experience I had last year when I was living in Nicaragua.  A man at a local Toshiba repair shop was nice enough to give me a boot disk full of repair and diagnostic utilities that fixed bad sectors on my hard drive and get it working in time to rescue my data before getting a new one.  It turned out that it was a physical problem with the drive.  I am going to give that a try if I can find the disk.  

Please, if anyone has a better understanding of why I can or cannot get ride of the corrupt journal or circumvent the missing journal inode, let me know here!  This seems to be a very illusive problem...

---

### Post by phineaus on 2007-12-13
So, I found the boot CD that I burned from this guy in Nicaragua, and it is full of utilities.  One is for bad sector recovery on damaged hard disks.  It has scanned nearly half of my 60gb drive so far and found and successfully recovered 71 bad sectors.  I have my fingers crossed that this will put my partition right again and let me boot linux to recover any data.  We shall see.  I will update here later tonight.

That said, if this program recovers all bad sectors it finds, and I still have the same issues with linux, that means that all of my issues lie within the structure of the filesystem, correct?

---

### Post by phineaus on 2007-12-14
I have lost my faith.  And I never even thought I was much one for faith in anything.  I ran a utility called Hard disk Regenerator that finds and recovers bad sectors.  It took all day, and found and recovered 277 bad sectors on the disk in question.  Upon reboot I still got error 17 from grub.  Then I tried to boot the LiveCD only to have it trip out with Buffer I/O errors and eventually throw me into Busybox.  I am not sure how I cannot even boot from the LiveCD..but its happening.  I love UBUNTU, and want to understand how linux works, but I really got dropped on my head this time.  And without any reason (despite having 10 plus years experience with windows and knowing just how something can go wrong without user intervention or cause).  This was not a physical hard disk crash it appears, but a failure of my filesystem.  A malicious virus?  Who knows.  Case closed without even the satisfaction of knowing what happened :-(

---

### Post by mozetti on 2007-12-14
I've been following your issues. While it initially started without anything you did, I think the reason you can't revive the partition is because you used testdisk. You made some very low-level changes to the partition table and IMHO, that's what put you into the unrecoverable position that you're in now.

I've had a few scares with GRUB errors, but I was able to get back to a working condition using basic tools. Although your initial problem started without user intervention or cause, manually changing the drive's geometry in testdisk probably contributed to your problems. Another thing I noticed, is that the tools were telling you it looked like your filesystem or drive were damaged from the start. I wouldn't be surprised if some sort of hardware failure contributed to the problem, too -- if disk regenerator found and fixed that many bad sectors on a partition that hasn't had anything done to it since it was shut down right before the error popped up, then something was not working correctly.

Don't be too quick to blame this on the OS. IMHO, this was a combination of bad luck and some bad decisions early on. Take what you've learned so far, re-install Ubuntu and hopefully avoid these problems.

FYI - if you want to increase your chances of keeping your data then you need to set up separate partitions. I **always** keep my data in separate partitions away from the OS. I also use a separate partition for /home. This way, if the OS corrupts then I just re-install it to the root partition and map all my data partitions and my /home partition to the fresh install.

For example, I've got 2 SATA HDDS (1x200GB and 1x300GB). I have the following partitions:```
/ - root
/home
/media/music
/media/video
/media/photo
/media/files
/media/data
/media/workspace
```

---

### Post by phineaus on 2007-12-14
Thanks Mozetti.  About the changes to disk geometry, I changed them back and re ran the same diagnostics with the same results before running Hard Disk Regenerator.  I wanted to rule that out as a possibility for the sake of my own sanity, because at the time I was very uncomfortable editing the partition table even based on someones or testdisks advice.

Yes, I do need to start from scratch.  This may be a dumb question, but how do I do that if I cannot even load the liveCD for gutsy?  I would like to leave my windows partition intact if possible, although that is expendable.  So ideally, I would like to format the 43gb linux partition and swap partition, then make new ones like you outlined above. 

I have read something about making installing grub and the mbr to a very small bootable partition because some bioses will only look in the 1st small bit of the physical disk for that information.  Is that the partition I need to make bootable with the kernel too (mounts at / root)?  Then if I am understanding correct, I should make another much bigger partition that mounts at /home where I can store all my data and keep it apart from the filesystem in the case of a similar crash in the future.  (I would make a number of specific partitions for each of my media types like you listed...but that seems like a lot for my needs)  I am not super experienced in organizing the partition table although I surely know more about it at this point.  

Finally, I was having some general issues with how fast Gutsy was running on this machine, and am a bit paranoid about case ventilation after this fiasco, so I think I am going to get a new case and motherboard (this one is from 2002 or something, and the case is a giant that has been around for almost 10 years).  For clarity and logistics purposes, would you recommend making those upgrades before installing a fresh copy of Gutsy and repartitioning?  At this stage of the game I have been using my laptop and have already lost the media and email correspondence from the last month or so (thankfully the rest was backed up on this laptop).  

Thanks again for your moral support and advice.

---

### Post by mozetti on 2007-12-17
If you plan on upgrading the motherboard, then definitely wait to re-install Gutsy until after you've done the hardware upgrades. Swapping a motherboard is a fairly major upgrade, and you're bound to run into problems if you install Gutsy, then put in a new motherboard.

As far as how to re-install, if you can get into Windows then load that up and nuke the partitions from there using **Disk Management**. After the linux partitions are gone, I'm assuming you'll be able to run the LiveCD and re-partition for Ubuntu and install Gutsy again. If you can't get into Windows, try the GParted LiveCD to delete the Linux partitions.

My partition scheme is probably a bit overboard, but it works for me. :) I'm not too sure about using a separate /boot partition because I've never had to do that. I'm sure there's plenty of documentation out there about it, though. For you, I'd do one of two things after you figure out whether to use a /boot partition:

1)Make a / (root) partition of 6-10 gigs and then make the rest of the drive a separate partition for /home.

2) Make a / (root) partition of 6-10 gigs, make a /home partition of 5+ gigs (total size is up to you), and make another partition (formatted as FAT32) using the rest of the space. This last parition is FAT32 so that both Ubuntu and Windows can access it easily. Any files you want to access from both OSs would go there, or you could use it to move files from one OS to the other by placing them in the FAT32 partition.

***Note*** Don't make your /home partition FAT32. FAT32 doesn't handle permissions, which Linux needs for the /home partition to operate. I'm pretty sure the system would be inaccessible if the /home partition was formatted as FAT32.

---

