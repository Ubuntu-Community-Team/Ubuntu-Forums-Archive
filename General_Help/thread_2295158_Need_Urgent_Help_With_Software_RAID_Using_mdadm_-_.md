---
title: "Need Urgent Help With Software RAID Using mdadm - Data Recovery Issue"
date: 2015-09-16
forum: General Help
---

### Post by ac2334 on 2015-09-16
Hello,

I need help with a situation that i am trying to resolve. Let me give some background to provide as much information as possible.

I have the 15.04 version of Ubuntu installed.

My goal is to reconstruct a software RAID 0 array that I had existing on a Western Digital My Book Studio II (4 TB) external hard drive (these were it's default settings). There was an issue with the controller on the hard drive and it was no longer recognized by any OS (I tried 4 different ones), but the data on both 2 TB drives remained intact. I took the drives out and put them in two external USB 2.0 enclosures and connected them to my Ubuntu setup.

I then ran the command: sudo mdadm --create /dev/md0 --level=0 --raid-disks=2 /dev/sdc /dev/sdd believing that this would "pull" the information from the existing RAID setup and place it on the newly mounted "md0" partition. It seemed that someone else had done this successfully on another forum, so I thought this was the correct step. However, because this RAID was not created under linux and was preexisting, it seems that the mdadm command may have overwritten very important data on my 2 2TB disks. 

Following the command, terminal reported "Array started" so that was no issue. But because there was no sign of a mounted /md0 partition, I had to create a filesystem on /md0 and chose ext3. Once this command was initiated it began a process that took about 15-20 minutes..it said writing inode blocks and when it was all done I had a new partition mounted in the dock that was 3 TB (??)

I understood mdadm to be non-destructive and thought that no harm could come to my original disks (the 2 TB drives) because the work is being done on the new partition (md0). I began freaking out because after more reading it seems that perhaps "assemble" not "create" may have been the better command to use. However, this RAID 0 setup was never created using mdadm so I can't be sure that assembly would even have worked.

After more reading, it seems that mdadm has certain safeguards to recognize existing array setups so I can only hope to recover from here.

The thing is, the entire 4 TB RAID 0 setup is HFS+ journaled because it was used entirely on a mac. I would like to think that I haven't just written an ext3 file system over my precious data.

Can somebody who has knowledge about this please help me or point me in the right direction. It is a time-sensitive issue to recover this data..

Thank you

---

### Post by metalfan49 on 2015-09-16
Hopefully I'm wrong, but I think you have made recovering your old data difficult in at least two ways. As you stated, when you want to bring up an existing array, assemble, and not create would be the path you'd want to go.  You could've done an mdadm --assemble --scan and hope it found your WD created array.  By creating, your overwrote the old with a new array.  Then, you created a new ext3 filesystem on the new array, making more changes to the drives and reducing the chance of recovery.  Maybe the array metadata is in a different location and a new WD My Book chassis could recover the array? Or some data recovery tool could attempt to look for viable data, but, the striping probably complicates that.

---

### Post by ac2334 on 2015-09-16
Thank you for your reply. As I understood the way that mdadm works...the creation of the /md0 is a "virtual drive" in essence so I don't think that anything on /sdc or /sdd should be touched. I never wrote any files to the mounted /md0 which would then write back to the 2 2 TB drives. I have confirmed from the mdadm instructions page that --create is used to create a new "drive" and that the mkfs ext3 command is the same as formatting a new drive. I don't think this would affect the 2 drives - I hope I'm right. If I'm wrong, can I reverse these changes at all?

Thank you

---

### Post by ac2334 on 2015-09-16
Can Testdisk be used to restore the proper filesystem (HFS + extended)?

If it can, all of my original data on both drives should still be intact..

I never wrote anything to /dev/md0

---

### Post by metalfan49 on 2015-09-16
I've never used TestDisk myself, hopefully it works for you and I'll have to remember the name in the future!  I'm slightly worried that either (or both) creating the new array and writing the new filesystem wiped out existing data or metadata on the disks.  Maybe TestDisk will be able to recover the original structure though.

---

### Post by mastablasta on 2015-09-17
Adam, I am afraid that I can not help you.

it looks to me like you formatted your data. you would now have to restore it in some way. you were using proprietary file system and a different (hardware) controller, so it would have been best to change/repair controller that failed.

mdadm is a software RAID solution where no controllers are needed as this part is done by software. hardware raid has this issue that controller can be ruined and then it's a pain to recover it. to prevent accidents we need to have a good backup solution. RAID is not a backup but is there to provide continuous operation in case of disk failure.  RAID0 is not really useful. sure, it joins two hard drives into one, but so what? one drive fails, you can loose everything. I am not sure why people use it. it was maybe useful when drives were small and you just had to add two together to get the disk space you needed. it acts kind of like a duct tape. now users seem to mostly just have problems with it.

so RAID1 and more (the useful numbers) doesn't safeguard against loss of data it only guards against disk failure. for that reason RAID is not a backup solution.

I had a OS drive failure (wasn't in RAID) and the backup image of that was not good. however it did have good setup&config files, so I reinstalled the OS, used the old configuration and loaded pre-existing mdadm array created in same OS.

---

