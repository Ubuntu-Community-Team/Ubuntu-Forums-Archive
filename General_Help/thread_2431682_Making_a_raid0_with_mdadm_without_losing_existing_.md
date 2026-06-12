---
title: "Making a raid0 with mdadm without losing existing data?"
date: 2019-11-20
forum: General Help
---

### Post by brisingre on 2019-11-20
Right now I have a raid1 of two 14tb drives on my file server. It's nearly full, so I'm adding a second raid-1 pair and moving to a raid1+0 configuration.

I created the new raid1 pair like this:

```
sudo mdadm --create dev/md/mirror_b /dev/sdc /dev/sdd --level=1 --raid-devices=2
```

I created an empty ext4 filesystem on it, then created the raid0 connecting them like this:

```
sudo mdadm --create dev/md/main_raid /dev/md/mirror_a /dev/md/mirror_b --level=0 --raid-devices=2
```

This created a new 28tb raid0 drive, as I expected. Unfortunately, it's just showing up as 28tb of "Unknown". 

I feel like I'm missing a step to get my files back. Is there a command to get mdadm to set up a filesystem with the files already on the drives? I'm trying to turn that 28tb of "Unknown" with a 28tb ext4 filesystem with 14tb of it already full.

I made a backup of everything before I started this process, so if I've ruined this and have no choice but to format the 28tb drive and start over, I can do that. But if there's a proper way to do this, it's worth it to me to learn what it is -- it will save me a whole day waiting for a 14tb file copy, and save a small amount of data that was written to the drive after I made the backup I'd be restoring from. 

If I did screw this up, what was the proper way to do it? Should I have created the raid0 with only the new drive pair, copied everything onto it, wiped the old drive pair, and then expanded the new raid0 to use it?

I'm definitely still a linux newbie so any and all help is greatly appreciated.

---

### Post by TheFu on 2019-11-20
And interest in using ZFS?  With that much storage, I'd really want the added protection of ZFS.

It is a best practice to always use partitions for RAID sets. Yes, you can use the entire disk, but then when those disks get repurposed, the uninformed will probably have issues. Or if a drive has to be pulled for any reason, someone else might think it is empty because there isn't any partitions marked as used for RAID.

If you can't use ZFS, any consideration in using LVM + RAID?  LVM has all sorts of migration techniques to change from different RAID levels, plus the ability to freeze snapshots for completely quiesced data backups, which mdadm RAID-only cannot.

---

### Post by brisingre on 2019-11-21
I could switch to a different raid tool. Now would definitely be the time, if I was going to.

Truth be told, I know nothing about ZFS or about LVM. I was just trying to keep it simple since I don't really know what I'm doing.

Could you explain a little more about the advantages ZFS has over mdadm? Added protection sounds good, but I'd like to know about the practical differences.

---

### Post by TheFu on 2019-11-21
You would learn 1000x more by setting up a tiny z-pool and playing around with 4 virtual disks for 30 minutes. There are lots and lots of intro-to-zfs or tutorial-on-zfs articles out there.

As for what it provides, the wikipedia article is better thought out than what anyone here can say.

My only warning is that ZFS should be used only for data at this point, not boot or OS storage.  Nothing that would get in the way of logging in.  If you were running Solaris, my answer would be completely different, but on Ubuntu - data only.

ZFS is like LVM + file system + remote mirror tool + storage caching + byte validation solution.

---

### Post by SeijiSensei on 2019-11-21
> **brisingre said:**
> I created an empty ext4 filesystem on it, then created the raid0 connecting them like this:

This created a new 28tb raid0 drive, as I expected. Unfortunately, it's just showing up as 28tb of "Unknown". 
Linux doesn't see a RAID device as different from any other storage device. You format the device after it is created. For instance,
```

sudo mdadm --create /dev/md0 --raid-devices=2 --level=0 /dev/sda1 /dev/sdb1
sudo mkfs -t ext4 /dev/md0

```
This creates an ext4 filesystem on /dev/md0.

---

### Post by TheFu on 2019-11-21
Using what you know already has lots of pluses.

So, let's think through how to convert a RAID1 2-partition setup to a RAID10 4-partition setup, using only mdadm.
[https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm) is very useful reading.

Be certain to read everything before starting.  

* the partitions must be sized exactly the same.
* I don't know how striping can be added to an existing RAID setup, so striping probably has to be accomplished first on the new disks.  Can someone confirm my thoughts are correct or not?
> 
Conversion between raid-0 and raid-10 is supported - to convert to any other raid you will have to go via raid-0 - backup, BACKUP, BACKUP!!! The code **does not** appear to support conversion between raid-1 and raid-10 which should be easy for a two-device array. 

* On the new disks, create a specifically sized partition using whatever tool you like. Use the same tool. While you are there, I'd ensure GPT is used for the table first.
* On the new disks, create a 2 disk RAID0 stripe.  Stripe size / chunk size is a decision you'll have to make.  I did some testing back when I moved from 320G disks to 2TB disks. Your best performance will be determined by the specific controller, connection, disks used.  For RAID10, the chunk size must be a power of 2.
* pick the layout style.  RTFM about this. Using "far" can create issues later, it says.
* After the array is assembled, pick a file system. I  use ext4 on mdadm storage and make it.
* Now you need to move the old data over to the new RAID0 disks.  rsync?  Restore from backup?

That will take a few hours, so working on the plan to add the mirror disks from the old disks.
* GPT
* partition, sized identically to the others.
* yes, total data wipe.
* [https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Raid_10](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Raid_10)

Found this: [https://www.linuxquestions.org/questions/linux-general-1/migrate-raid0-array-to-raid10-with-mdadm-740104/](https://www.linuxquestions.org/questions/linux-general-1/migrate-raid0-array-to-raid10-with-mdadm-740104/) for going from RAID0 to RAID0+1.  The commands they show assume no partitions were used, but it is mentioned that partitions should be used.  Ends up in a RAID0+1 setup, not a RAID1+0 setup. There are some failure modes with RAID0+1 that aren't good.  If you will expand with more disks later, RAID10 is important.  With just 4 disks, it seems to be a minor risk since there is already a likely problem if 2 disks fail.

[https://serverfault.com/questions/145319/is-there-a-difference-between-raid-10-10-and-raid-01-01](https://serverfault.com/questions/145319/is-there-a-difference-between-raid-10-10-and-raid-01-01)
> Unless your circumstances are exceptional, you should never use 0+1.

So, the best answer seems to be - wiping all the data, installing all 4 disks and telling mdadm to use RAID10 from the beginning.  Then restore the data from backups into the array.

I have 2x2TB RAID1 arrays for virtual machines.  All other systems don't use RAID.  Everything has automatic, daily, versioned, backups.  My new virtual machine server doesn't use RAID.  It is on a quality SSD with 20% unallocated storage for slack use.

**Work story:**
At work, long ago, they setup a 16-wide RAID10 setup for a critical DBMS.  After 4-wide striping is done, the extra disks don't really add much performance. This was on very high-end, expensive, fibre, storage. I was just the project tech architect. The DBA and SA teams made the decisions about this tuning.  4-wide stripes provide 80% of the theoretical performance gains, so going to 8, 16, 64-wide strips can only help, at most, 20% more.  Dealing with wider strips is a hassle in an enterprise with shared storage frames.

That was all before SSDs were available.  These days, I bet that entire DB is on SSD storage in RAID10, thought I've been to some storage conferences where they say mirroring enterprise SSDs is a waste because that type of SSD hardly ever fail.

---

### Post by brisingre on 2019-11-22
Thanks for all these detailed responses! You've been really hugely helpful.

Sounds like I definitely have to wipe the raid and copy in from backup. That's fine, I sort of expected that.

It  also seems like Raid10 isn't really what I want for future  expandability, I'll be switching to either LVM or ZFS. Probably LVM, ZFS  looks complicated? But I'm not done my research.

---

### Post by TheFu on 2019-11-22
It would be LVM + some file system
or
ZFS.  ZFS includes volume management, so using LVM with it wouldn't be smart with ZFS.

LVM includes the mdadm code, so it probably has the same RAID10 limitations.  LVM shines when it comes to being flexible about storage allocations and moving PVs to different storage devices. Check out pvmove.  I've used that a few times the last few months, but not with any RAID storage.

ZFS has some preferences with certain numbers of disks.  I think most people use RAIDz or RAIDz2 with their ZFS deployments.  

There's nothing wrong with using mdadm if that is your level of comfort and you aren't interested in head scratching every time you want to / need to change storage a little. There is much to be said for following KISS.  Do you intend to be a storage admin or just want to set this up for 3 yrs and forget about it?

---

### Post by brisingre on 2019-11-22
After reading some ZFS tutorials it's looking more plausible to learn it, I'll mess around some on a virtual machine this afternoon. It's not like I really know mdadm either, no matter what I'm learning as I go here. I might as well do it right.

My goal is probably closer to set this up for 3 years and forget about it. But I will have to expand it periodically, at least. I'll explain my use case.

I'm the only user but I've got several machines connected to it. It's storing a giant video library. 



I'm developing a video player that works sort of like broadcast TV. You make "channels" which are playlists of video files that play in a never-ending loop. 

When you switch to a channel it chooses where to start in the playlist based on the system time, so it's as if the channels continue to play whether or not you're watching them, like an actual TV channel. Nothing complicated but it's fun. 

It expects a big video library somewhere on your computer, but a network folder is fine -- you can run TV Simulator on pretty basic hardware and keep your storage elsewhere on the network, which is especially nice if you have more than one screen.

 I kept my library on a basic windows fileshare from my main PC until I ran out of space, then I decided to do things properly and put together a dedicated fileserver with real redundancy and a plan for expansion and stuff. 

I hadn't spent more than a day or two on linux before this project and it's been rough, I had a ton of random intermittent failures that I only managed to pin down as a defective ram stick last week, but it's basically been working. 

Until a couple weeks ago when I decided to expand and realized my expansion plan had basically been "assume it'll be easy and make backups" and it wasn't easy but at least I made backups and here we are.



I basically have the same concerns anybody putting together a RAID does. In order of most to least important:

1. I don't want this thing to go south and lose my whole whole library.  There's a lot of cheap hardware in this system, so it has to be tolerant to  failures. 
2. I gotta be able to add disks. I have 5 right now but only 4 are free to create the RAID because 1 is holding the backup. The system can support 10. 
3. I'd like it to be fast to read. Every time you switch channels there's a moment of lag while it loads the new video file. That isn't all drive reading, some of it's decoding and general software slowness, but it's good to read fast. Writing fast doesn't really matter, most data on this thing only gets written once.
4. I'd like to use space efficiently. I can keep throwing disks in this thing for a while, so this isn't a huge deal now, but once I hit my 10-disk limit I can imagine that the difference between RAID10 and RAIDz2 will be massive.

mdadm makes it really hard to add disks so I want to switch to something that makes it easy, and if I'm switching raid levels, now would be the time.

---

### Post by SeijiSensei on 2019-11-22
> **brisingre said:**
> mdadm makes it really hard to add disks so I want to switch to something that makes it easy, and if I'm switching raid levels, now would be the time.
Doesn't look that hard to me:
```
mdadm --grow /dev/md0 --add /dev/sdc1 --raid-devices=3
```
Without the --raid-devices parameter, the new disk would be treated as a spare.

See: [https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Grow](https://raid.wiki.kernel.org/index.php/A_guide_to_mdadm#Grow) and [https://raid.wiki.kernel.org/index.php/Growing](https://raid.wiki.kernel.org/index.php/Growing)

I've not done this so I don't know how the filesystem format is extended to the new device.  I also never use RAID 0.

---

### Post by TheFu on 2019-11-23
I don't use RAID for media files.  I do have backups of those files, however.  RAID is just too much hassle when I know that changing a failed disk for the backup disk is about 15 seconds of my time.  One failed disk about of 10 is a minor thing.

For backups of media, I use an external USB3 4 disk array. For backups, USB3 is fine.  I wouldn't use it for any transactional needs. The USB-storage protocol is limited.  However, relatively cheap eSATA external arrays can solve that issue.  Just get a quality LSI JBOD SAS controller and use a SAS to SATA cable to have 4x the disks connected.  I've seen a BSD-compatible JBOD LSI 2 port PCIe controller for $70. That's an easy way to add 8 more HDDs.  Why does BSD matter?   When it comes to great compatibility, if a vendor makes it BSD compatible, it will almost certainly work well on Linux.  Never trust hardware boxes that say "Linux Supported" since it might have been for 1 kernel running v2.6.x in 2004, but nothing since.  I've been burned buying a RAID controller with exactly that situation.  We really need for all the HBA controller features to be included in the kernel driver tree for the best possible, least hassle, support under Linux.

I wouldn't jump into RAID with just a few weeks of Linux experience.  There are better ways to spend your learning time now than RAID.  IMHO.   Like learning the first 200 pgs or so of this: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  Anyone creating software needs a strong background in Unix security to avoid creating trivially hacked systems.

---

### Post by SeijiSensei on 2019-11-23
I have all my media files on a 3 TB RAID1 formatted as ext4 with about 500 MB free.  There are a bunch of other things on that device that I could dispose of if I need more space.

---

### Post by brisingre on 2019-11-30
Hey guys --

Just wanted to come back to say thank you, give an update on my progress, and officially mark this resolved.

I've got my backup copied back onto an mdadm raid1, so it's stable and safe for now. I used partitions rather than whole disks this time, so that's a small improvement at least. :P

I'm slowly working on trying to transition to ZFS, I'm leaving some disks free so I have spares to experiment with. It's going well so far I think. 

Everybody here has been super helpful. Thank you all!

---

