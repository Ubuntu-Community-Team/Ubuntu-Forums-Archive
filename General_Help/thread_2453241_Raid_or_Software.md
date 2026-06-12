---
title: "Raid or Software?"
date: 2020-11-05
forum: General Help
---

### Post by ubulove89 on 2020-11-05
Hi all,

At home i few old computers with data on it because i like to photograph. This is about a 13TB. I have 4 disks om sata 6 from 3 to 4 TB. No i am looking for different solutions to combine the disk as one disk volume or with software to virtualize that. I know that disk failures will ruin my data on it, But i bought a sata + Hardisk to pull data from the combined harddisk with rsync or something.
The reason why i want to combine those disks is to **speep up** data transfers. Because one single shot of my camara is sometimes at "worst" settings 120Mb per picture and hundreds of Gbs of movies i toke (all RAW data), so when i try to load an entire collection it takes ages before is can see my pictures/movies. In this way i can speed up, and stay safe!

I was thinking about LVM on the smaller disks and rsync for the backup to the big one early in the morning.
Do you guys have a nicer idea to do this? I also like to have simple solutions, but this time i prefer quality and performance over doing things the simple way!

i prefer:
full usage of the 3 or 4 gb disks, i have one 4 tb and i dont want a 1tb lost
speeding things up!
easy to defragment the "LVM" disk
you will not say to buy a SSD, have you seen those prices of 12TB+?

Thanks in advance,

---

### Post by TheFu on 2020-11-06
There is reality and fantasy land.

Every disk added to a single RAID file system increases the possible failures.  For larger disks, say anything over 1TB, I only use RAID1.  For backups, I don't use RAID.  My backups don't use anything complex and are limited to 4TB chunks.

Complicated storage is more hassle than it is worth.  People are always using this stuff and think it is great until there is an issue.  Then they uncover how important excellent backups are. Sometimes the only answer for RAID failures is to wipe the array and start over, using backups.

If you want performance, switch to SSD. If you want high performance, switch to NVMe SSD.  

Spinning disks are for safety, not performance. Because of the current costs, you'll want to have actively used files on the SSD and migrate older, unused files, to spinning disks.  This is called **tiered storage** and has been part of enterprise storage for decades. 

If you aren't rich, this is your reality.

At home, I use LVM and I use RAID. Due to timing for each skill, I've not used both outside of work and my work didn't use Linux for storage, we had EMC and netapp storage.  Long ago, I setup a 3 disk LVM LV in RAID0 - everything was fantastic for about a year, then one of those disks failed.  All the data on all 3 disks was lost.  At the time, I didn't have backup religion, so I lost about 80% of that data.  I was in denial for a few months. Heck, I may be able to find one or two of those 80GB IDE HDDs even today. There's always hope, right?

I use RAID1 for virtual machines. When a disk failed, it kept going and at the earliest time, I'd add in a replacement for the failed partition.  This has happened for a few disks over the decades. If you know what you are doing, it isn't hard, provided you don't let the failure go on and on for too long. Monitoring SMART data is a weekly thing here. The performance of the RAID1 storage really isn't all that great.  See, if you don't use striping, then you don't get better performance. Today, the only way I'd use striping for anything that wasn't 12-hour scratch storage is by using RAID10.  There are very good reasons to avoid RAID0+1. 
For scratch storage, just get some NVMe SDD and use that. Those are 10x the speed of even SATA SSDs if in a x4 PCIe slot. There just isn't any comparison. No need for RAID.

But in the end, solid backups are the core of our data protection.

In terms of combining storage, that is something that we all have to do, hopefully, before a HDD fails. I've seen 14TB HDDs on sale recently, though I'd never use USB storage in RAID-anything. RAID really needs the SATA, eSATA, or SAS storage protocols. Every 3-8 yrs, we should be replacing our storage ... or at least migrating from older to newer based on the best information available about each disk.  I have a few 11 yr old WD 1TB "black" HDDs with SMART data that shows ZERO problems. I also have a number of 3 yr old, cheaper, HDDs that are beginning to not-so-great SMART data.  I don't like surprises when it comes to storage failures.

---

### Post by ubulove89 on 2020-11-06
Thanks, but i have 2x1TB nvme drives already for my actual data. My older data needs speedy access to because i work sometimes on projects that require old data and speedy editing because of press/politic content. Its really hard to find sometimes a single shot. within 30 minutes, that is killing my sell price sometimes...

I have the older disks, that are high quality disks (sata) that are mostly used in the smaller servers. Even after 10 years and sometimes longer, but then you always need to buy the "bigger" disks (after launch) you can buy the same disk from the vendor. Also i have a backup plan for a 14 TB disk. So i would say i will still give it a go because of my backup plan. What you said about the raid combinations is interesting thing, i will give it a look!
I am not planning on 12x1 TB SSD or bigger SSD... The prices are to huge. Even it is hard to store so much NVMe disks in a single computer, or buying the more expensive big ones. The problem is the investment (for me i.e.) of multiple SSDs is not worth it yet.

Thanks!

---

### Post by TheFu on 2020-11-06
I did some work with professional photographers and videographers around 10 yrs ago. They had SAN storage and really tried to store as much descriptive metadata with each shot as they could. I was amazed that most shots had 20-100 items of metadata just to describe the image contents, not the technical stuff.

The guys with less money used commercial SAN devices like you'd find on SmallNetBuilder.com. 

If you get away from "desktop" computers, you can easily find systems that will support 20+ disks.

Learned about an image categorizing tool a few weeks ago. It uses AI and has to be trained before it becomes useful. In a business, this would probably take more effort than just manually adding metadata as the shots come in.  OTOH, wouldn't it be nice to get a night, snowflake, Eiffel Tower, moon image or 20 with just 1 query?  Or perhaps Pet&#345;ín Tower would be close enough, provided all the other aspects are included?

It is all about the metadata.  Good metadata prevents having to look through 200 images.

---

### Post by Impavidus on 2020-11-06
The human brain can't process a megabyte per second, so if you use the human brain to process the images, you don't have to access more than a megabyte per second, provided that you use clever indexing and thumbnails (which can still be the size of your screen) with lossy compression. I think that would be the smart solution.

---

### Post by hk42 on 2020-11-07
IMHO combining different origin/size drives in Raid is a very bad idea.
I have been using Raid0 for more than 10 years but I started them
with brand new identical drives.
In that case I believe it increase the reliability at the expense of
 power consumption.
There was also a real improvement in speed but now with SSD's it is
not useful.
Having a single huge partition is not a good idea as far as backup or
repair are  concerned.

---

### Post by TheFu on 2020-11-07
> **hk42 said:**
> IMHO combining different origin/size drives in Raid is a very bad idea.

This is partially why the "best practice" for all RAID is to use partitions, so that finer controls over the sizes for each RAID device can be controlled AND when it is time to replace 1 of the HDDs, the whole drive size of the new HDD isn't so critical. Making a partition of identical size to other partitions is much easier than trying to get slightly different HDD sizes to work in RAID.

---

### Post by ubulove89 on 2020-11-11
> **Impavidus said:**
> The human brain can't process a megabyte per  second, so if you use the human brain to process the images, you don't  have to access more than a megabyte per second, provided that you use  clever indexing and thumbnails (which can still be the size of your  screen) with lossy compression. I think that would be the smart  solution.

That does not always work, that is why asked you guys on this topic




Thx for the replies people, i can move on!

---

