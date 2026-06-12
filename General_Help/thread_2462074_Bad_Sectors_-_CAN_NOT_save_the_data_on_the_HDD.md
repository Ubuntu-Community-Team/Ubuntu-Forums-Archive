---
title: "Bad Sectors - CAN NOT save the data on the HDD"
date: 2021-05-13
forum: General Help
---

### Post by amjjawad on 2021-05-13
Hi,

Hardware: ThinkPad E590, Core i5 8th Generation, 12GB RAM and 1TB HDD.
Software: Ubuntu 18.04

Total running time: 10 weeks.

Long story short:
[LIST]
[*]Despite the fact that I bought this laptop exactly (2) years ago, I have used it for ONLY 10 weeks.
[*]I bought it without any OS installed.
[*]I decided to use Ubuntu 18.04 after I have used official variants from 2011 until 2019.
[*]The current OS is the one and only OS that I have installed on that machine (laptop).
[*]When I started to use it, I tend to use 'Hibernate' more than 'Shut Down'.
[*]I noticed recently some crashes in my 'Browser' which is 'Chromium' and the machine is kind of slow. In fact, the performance, in general, was bad when I do 'Hibernate'. However, recently, it became more noticeable.
[*]A reboot/restart was a good choice to get things back to normal.
[*]Yesterday (12-May-2021 Sydney Time), something happened: couldn't search anything on google as I was in need to get some information. The tab was crashing over, over and over again. I thought to reboot the machine because I didn't shut it down for a quite sometime. I thought, as usual, that would solve the whole thing. Once that done, the whole laptop crashed.
[*]I got all kind of weird errors that I have never ever seen since I have started using GNU/Linux back in 2010.
[*]After several hours and countless tries, I managed to get to (**initramfs**) and managed to run (**fsck**).
[*]Yet again, errors that I have never seen before. Such as "Inode 3670112 seems to contain garbage".
[*]Tried my best to get to a point where I can at least understand what is happening so that I could save the day and at least rescue the data, but nothing happened.
[*]Finally, managed to get in after logging in to my OS.
[*]Nothing was working except 'GParted'.
[*]Rebooted with the LiveUSB inserted to one of the USB Port and got into the Live Desktop.
[*]Tried to use 'Disk' to check the HDD and, to my shock, it shows that the HDD has 'Bad Sectors', despite the fact that I've been using the machine for only (10) weeks!
[*]Here is the HARDEST PART. I managed to access the '/home' partition. While I was trying to save the data, the copy process got crashed and I couldn't save anything whatsoever.
[*]I have only (3) partitions on that machine: '/' and 'SWAP' and '/home'.
[*]The root partition is 100GB. The SWAP Partition is 14GB. The home partition is more than 800GB.
[*]I tried to resize the '/home' partition by reducing the size but 'GParted' crashed.
[*]I tried to reduce the size, aiming for 'Dual-Booting' but that wasn't successful.
[*]I am super sad, have anxiety and stress because all my lectures (videos) for (2) months are stored there.
[*]Now, I'm totally stuck. I can't do anything whatsoever.
[*]EVEN WORSE, my NEW External HDD (1TB) which I bought long ago, I tried to plug it to save the data but it crashed and it's a hardware issue 100%. So, double losses so far!
[/LIST]

**What exactly I need to do?**
[LIST=1]
[*]SAVE my data.
[*]Make sure the saved data is working just fine.
[*]Try to save the laptop (HDD).
[/LIST]

I suspect it is a software bad sector but I can't verify that.

Again, my priority is saving the data that is, so far, refusing to be saved.

If I can fix the bad sector, in case it is a software one not a hardware issue, that would be even better. If not, then there is noting I can do.

My data must be saved and you may ask, why I haven't done a backup?
Well, because:
A- The laptop was new. I never thought this will happen.
B- Because the laptop was new, I was using it as a backup machine for my files.
C- I never thought 'Hibernate' might be the cause behind this so I didn't do the backup.

I am not here to be blamed. I'm here seeking help.

Thank you in advance! 

P.S.
Please note, I can't use that machine so posting some information, logs, etc is hard.

---

### Post by dino99 on 2021-05-13
Have you tried to copy that faulty /home to an other device ? (do it from that other system device)
But keep in mind that the less done on that faulty hdd the better it is (despite you already have done a lot)

---

### Post by amjjawad on 2021-05-13
Hi and thank you for your post.

> **dino99 said:**
> Have you tried to copy that faulty /home to an other device ? (do it from that other system device)
But keep in mind that the less done on that faulty hdd the better it is (despite you already have done a lot)

Perhaps I didn't explain myself very well.

Indeed, I have tried that.
However, it failed.

---

### Post by amjjawad on 2021-05-13
Here are some screenshots. It is getting worse!

---

### Post by ActionParsnip on 2021-05-13
"software bad sector" isn't a thing. A bad sector is on the physical drive, not software.
If your data is important then why do you not have regular backups? What if the drive totally fails? Where is your data?

---

### Post by amjjawad on 2021-05-13
> **ActionParsnip said:**
> "software bad sector" isn't a thing. A bad sector is on the physical drive, not software.

This:
[https://www.datanumen.com/blogs/hard-vs-soft-bad-sectors-hdd-different-causes-solutions/](https://www.datanumen.com/blogs/hard-vs-soft-bad-sectors-hdd-different-causes-solutions/)


> **ActionParsnip said:**
> If your data is important then why do you not have regular backups? What if the drive totally fails? Where is your data?
That did **NOT** solve my problem. Kindly read the last paragraph in my OP.

---

### Post by dragonfly41 on 2021-05-13
Faced with these errors I would personally try a LiveUSB to fix bad sectors through command line.

[https://www.amolak.net/fix-hard-disk-bad-sectors-in-linux/](https://www.amolak.net/fix-hard-disk-bad-sectors-in-linux/)

---

### Post by tea for one on 2021-05-13
Have you considered Clonezilla?
[https://clonezilla.org/](https://clonezilla.org/)

Prepare a USB stick with Clonezilla
Clone your /home partition
Beg, borrow, steal another PC
Restore your cloned partition to a different PC
Check your data for damage/corruption etc.

---

### Post by amjjawad on 2021-05-13
Hi and thank you for your reply.

> **dragonfly41 said:**
> Faced with these errors I would personally try a LiveUSB to fix bad sectors through command line.

[https://www.amolak.net/fix-hard-disk-bad-sectors-in-linux/](https://www.amolak.net/fix-hard-disk-bad-sectors-in-linux/)

```
  
ubuntu@ubuntu:~$ sudo e2fsck -cfpv /dev/sda1
/dev/sda1: Updating bad block inode.
Error reading block 9262 (Input/output error).  

/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)
ubuntu@ubuntu:~$ 


```

---

### Post by TheFu on 2021-05-13
If a LiveCD or Try Ubuntu environment running from a flash drive are failing, then the computer hardware is dying. Probably something inside the motherboard.  Initially, it looked like it could just be the original HDD, but the alternate boot media having problems moved the issue.

To get data off a failing HDD, 
a) stop using it for anything other than safe copying to a new disk.
b) use a different computer.
c) Take the HDD out that has the data you want and connect it to a different computer that supports 2 storage devices and can boot from a USB-flash Try Ubuntu environment.
d) install **ddrescue** - sudo apt install ddrescue
e) use ddrescue to perform a bit-for-bit copy FROM the source HDD to the target HDD.  Don't get those backwards.  ddrescue is designed to get as much data as possible from storage. The target drive will be completely wiped.  The target drive needs to be at least as large as the source drive.

Let ddrescue run over night - perhaps longer.  There is output showing progress of the copying and how the errors are being handled. Multiple passes can be used to attempt to get more data from difficult sectors copied.

Just because ddrescue can copy the data, that doesn't mean it is fully recovered.  On really bad disks, the drive might fail. This was going to happen already.  All storage devices fail.  Our goal is to have good backups BEFORE that happens.  For really important data, we need it stored in 3 different places.

If you do get a copy onto a new HDD, that is now the primary storage for that data and you need a new, fresh, backup ASAP.  Cloning isn't really an efficient backup. It is a way to move from one disk to another, if you don't have a better option. There are many, many, better options than cloning, unless the source HDD is failing. Then the options are limited - or cost $3000.

---

### Post by ActionParsnip on 2021-05-13
> **amjjawad said:**
> This:
[https://www.datanumen.com/blogs/hard-vs-soft-bad-sectors-hdd-different-causes-solutions/](https://www.datanumen.com/blogs/hard-vs-soft-bad-sectors-hdd-different-causes-solutions/)



That did **NOT** solve my problem. Kindly read the last paragraph in my OP.

"Soft Bad Sectors" are not "Software Bad Sectors"

---

### Post by mikewhatever on 2021-05-13
Bad sectors are bad sectors. Data corruption due to a power failuer is not it.
I am afraid that article is pure nonsense.

---

### Post by ActionParsnip on 2021-05-13
> **mikewhatever said:**
> Bad sectors are bad sectors. Data corruption due to a power failuer is not it.
I am afraid that article is pure nonsense.

Exactly

---

### Post by amjjawad on 2021-05-13
Hi and thank you for your reply.

> **tea for one said:**
> Have you considered Clonezilla?
[https://clonezilla.org/](https://clonezilla.org/)
No, I haven't thought about it. Appreciate the suggestion.
However, with the current situation, I am not even sure if this is going to help/work or not?

I will give it a go!

> **tea for one said:**
> Prepare a USB stick with Clonezilla
Clone your /home partition

I was reading the website and it mentioned:

> The destination partition must be equal or larger than the source one.   

I am not sure what does it mean?
Does it mean, if the drive I'm trying to clone is 1TB so the destination should be equal or larger?
Or, it means the size of 'files' that I'd like to clone so the destination drive should be equal or larger?

I have never used this software before.
Whenever I wanted to do a backup, I simply copy and paste. Old school. 

> **tea for one said:**
> Beg, borrow, steal another PC
Restore your cloned partition to a different PC
Check your data for damage/corruption etc.

Steal?
I don't have to steal.

If and only if I managed to do that successfully, that would be great. 
The most important part is, I check the data, if saved, for damage or corruption.

I'll try and report back.

---

### Post by tea for one on 2021-05-13
In this regard, cloning is not strictly a back-up, it is just a means of transferring data from a possibly damaged drive to a healthy one.

You could first try [COLOR="#0000FF"]partition[/COLOR] to [COLOR="#0000FF"]partition[/COLOR] clone using devices (rather than images)
Boot up a live session of Clonezilla
Select only your /home partition as source (i.e. less than 1TB)
Use your new 1TB disk as destination (i.e. greater than your 877GB home partition)

When the process has finished, use another Ubuntu PC to see if you can access the files as a normal external drive.

Fingers crossed.......

---

### Post by amjjawad on 2021-05-13
Hi and thank you for your reply.

> **TheFu said:**
> If a LiveCD or Try Ubuntu environment running from a flash drive are failing, then the computer hardware is dying. Probably something inside the motherboard.  Initially, it looked like it could just be the original HDD, but the alternate boot media having problems moved the issue.

At the beginning, I thought it was the RAM. Never thought it could be the HDD. Never thought a machine that was running only for 10 weeks might fail so miserably like this.


> **TheFu said:**
> 
To get data off a failing HDD, 
a) stop using it for anything other than safe copying to a new disk.
b) use a different computer.
c) Take the HDD out that has the data you want and connect it to a different computer that supports 2 storage devices and can boot from a USB-flash Try Ubuntu environment.

I don't have any machine here that support (2) storage devices.
Any Plan B?


> **TheFu said:**
> 
d) install **ddrescue** - sudo apt install ddrescue
e) use ddrescue to perform a bit-for-bit copy FROM the source HDD to the target HDD.  Don't get those backwards.  ddrescue is designed to get as much data as possible from storage. The target drive will be completely wiped.  The target drive needs to be at least as large as the source drive.

If that is the case, I don't even a HDD that is as large as the current one.
If **'ddrescue' **will copy the entire failing HDD, regardless of the used sectors, then I can't offered that.
If it will only move the used sectors, I can handle this.

> **TheFu said:**
> 
Let ddrescue run over night - perhaps longer.  There is output showing progress of the copying and how the errors are being handled. Multiple passes can be used to attempt to get more data from difficult sectors copied.
Yes, I will leave it overnight, that in case it will work. Let's see. 

> **TheFu said:**
> 
Just because ddrescue can copy the data, that doesn't mean it is fully recovered.  On really bad disks, the drive might fail. This was going to happen already.  All storage devices fail.  Our goal is to have good backups BEFORE that happens.  For really important data, we need it stored in 3 different places.
I deserve this. I have learned the lesson the hardest way.

> **TheFu said:**
> 
If you do get a copy onto a new HDD, that is now the primary storage for that data and you need a new, fresh, backup ASAP.  Cloning isn't really an efficient backup. It is a way to move from one disk to another, if you don't have a better option. There are many, many, better options than cloning, unless the source HDD is failing. Then the options are limited - or cost $3000.
3,000$?
I can buy 3 new laptops with 3 new eternal HDD!
Oh well, I am learning the lesson yet again the hardest possible way.

I am not sure if this is going to work or not?
One way to find out.

However, I just need to know:
If I have no laptop that support (2) storage devices, what am I supposed to do?

---

### Post by TheFu on 2021-05-13
> **amjjawad said:**
> Hi and thank you for your reply.
Nobody is born knowing these things. It took me over a decade as a programmer before most of this sunk into my bonehead. Then it took a few massive data-loss events before I actually did something - which was not perfect, but better than nothing.  Then I had an other massive data loss event and got backup religion. Since that time, I've never lost more than 1 day of new data.

> **amjjawad said:**
> At the beginning, I thought it was the RAM. Never thought it could be the HDD. Never thought a machine that was running only for 10 weeks might fail so miserably like this.
Run time says nothing about treatment.  If it has been sitting on a comfy shelf with no vibrations and was never moved, that's very different than riding a bus or in a subway or in a backpack.  Hibernation, standby, and other modes that don't completely shutdown the OS and remove power could have an impact too. IDK.  When ever I move my laptop from 1 building to another - driving, walking, whatever, it is powered off, 100%, completely.

> **amjjawad said:**
> I don't have any machine here that support (2) storage devices.
Any Plan B?
How is this possible?  No USB ports?  Really?

> **amjjawad said:**
> If that is the case, I don't even a HDD that is as large as the current one.
If **'ddrescue' **will copy the entire failing HDD, regardless of the used sectors, then I can't offered that.
If it will only move the used sectors, I can handle this.
Clonezilla and all imaging bit-for-bit tools work this way.  So does ddrescue.  They are dumb.  They want to copy 1 byte at a time from Disk A --> Disk B.  So ... disk B needs to be at least as large as Disk A, the source.  No way around that when data recovery is the goal.  Now, if you are doing file-based backups, then just the amount of storage necessary to hold the files is required. Cloning a disk to an image file can be sent through compression tools, but as new as you appear to be, I'm loath to attempt to explain that. It would be a 90% chance of failure.

> **amjjawad said:**
> Yes, I will leave it overnight, that in case it will work. Let's see. 
If your target disk isn't at least as large as the source, don't.

> **amjjawad said:**
> I deserve this. I have learned the lesson the hardest way.
We all do. That's life.  Learn from this.
Story ... not important:
> **amjjawad said:**
> 3,000$?
I can buy 3 new laptops with 3 new eternal HDD!
Oh well, I am learning the lesson yet again the hardest possible way.

$3000 is for a professional data recovery service. They many need to replace controllers, platters, most of the insides before they can attempt recovery, assuming the media/platters aren't harmed already.

> **amjjawad said:**
> I am not sure if this is going to work or not?
One way to find out.
Yep. But it probably won't if the target disk isn't larger than the source disk.  You could try file-based backups - and I would. We don't really know what the problem is. If it is the motherboard, then you'll need to borrow someone else's computer for this stuff.  BTW, you can run a desktop on a $50-raspberry Pi, if you are really stuck for cash.

We zoomed in on the HDD being the issue based on the subject of this thread.  Did you happen to check the SMART data yet?  That is normally how people check that.  It could be just a bad cable too. SMART usually shows that as ECC errors and Read-Errors.

> **amjjawad said:**
> However, I just need to know:
If I have no laptop that support (2) storage devices, what am I supposed to do?
Again - your laptop doesn't have USB ports?  You can put almost any storage HDD/SSD into a cheap external USB enclosure.  I've seen these for $9.  I have a number of them - all sorts.  I prefer the "Dock" type, which support 2 HDDs over 1 USB3 connection. Then I can load raw drives into the "dock" and gravity holds it in place. Works with 3.5 and 2.5 inch SATA drives.  They run as fast as the drive would internally (almost always), since the "dock" has an external power and USB3 bus speeds are faster than all but the fastest NVMe drives anyway.  Think I saw one of these dual Docks for $25 a few months ago during a sale.  That's USD.

I'm not convinced the HDD is really the issue.  A cracked motherboard (physically cracked) can create short circuits.  

**Story ... not important:**
I've seen this a few times over my career.  I once dropped my personal laptop about 8 inches from a low couch to the floor.  That system never booted again.  The motherboard power connection was harmed.  It was just over 1 yr old, so out of warranty.  At the time, my credit card doubled the warranty on purchases, so I just needed to provide an official estimate to fix the problem and they'd reimburse me.  It was a $850 laptop. They gave me $650, since it has been used over a year.  I shopped about for a replacement about 4 months - I have multiple computers and didn't need a laptop at the time.  This was in 2011 ... and I still have that replacement laptop today. It is on the 3rd HDD now and I use it almost every day. It hasn't moved from the location since about 2013 when I moved to a very light, 2lb, laptop.

---

### Post by amjjawad on 2021-05-19
[ATTACH=CONFIG]288514[/ATTACH]

Is this normal?
Have you ever seen something like this before?! 

P.S.
I'll get back to the replies on this thread hopefully soon. I'm not ignoring anything.

---

### Post by amjjawad on 2021-05-19
> **TheFu said:**
> Nobody is born knowing these things. It took me over a decade as a programmer before most of this sunk into my bonehead. Then it took a few massive data-loss events before I actually did something - which was not perfect, but better than nothing.  Then I had an other massive data loss event and got backup religion. Since that time, I've never lost more than 1 day of new data.
Learn by doing, +1 for that approach. However, it is really painful. I had stress and anxiety over this issue, that is why I didn't reply earlier.


> **TheFu said:**
> Run time says nothing about treatment.  If it has been sitting on a comfy shelf with no vibrations and was never moved, that's very different than riding a bus or in a subway or in a backpack.  Hibernation, standby, and other modes that don't completely shutdown the OS and remove power could have an impact too. IDK.  When ever I move my laptop from 1 building to another - driving, walking, whatever, it is powered off, 100%, completely.
I don't know but I think the excessive use of Hibernate might be the real cause, not sure and can't verify that. 

Lesson learned. I'll not use Hibernate ever again whether it was the cause or not!

> **TheFu said:**
> How is this possible?  No USB ports?  Really?
I thought you were referring to internal '2nd' drive.
Yes, of course I have USB ports.
However, I don't have anything (hardware) to connect any drive to the laptop via the USB ports. 
I'm trying to use whatever I have at home instead of buying new stuff. 


> **TheFu said:**
> Clonezilla and all imaging bit-for-bit tools work this way.  So does ddrescue.  They are dumb.  They want to copy 1 byte at a time from Disk A --> Disk B.  So ... disk B needs to be at least as large as Disk A, the source.  No way around that when data recovery is the goal.  Now, if you are doing file-based backups, then just the amount of storage necessary to hold the files is required. Cloning a disk to an image file can be sent through compression tools, but as new as you appear to be, I'm loath to attempt to explain that. It would be a 90% chance of failure.
I'm not new but I've never faced this very issue ever before. 
Since 1999 until now, never had to deal with a similar situation! 

I personally prefer file-based recovery or backup. 
However, in my case, I am not sure if that is even possible or not?!


> **TheFu said:**
> If your target disk isn't at least as large as the source, don't.
Yes, until this moment, I have no drive that is as large as the dying/dead drive.


> **TheFu said:**
> We all do. That's life.  Learn from this.
Undoubtedly, I will sure do.


> **TheFu said:**
> $3000 is for a professional data recovery service. They many need to replace controllers, platters, most of the insides before they can attempt recovery, assuming the media/platters aren't harmed already.
I found a company here in Australia and I'll try to call them tomorrow. At least, a rescue plan!


> **TheFu said:**
>  Yep. But it probably won't if the target disk isn't larger than the source disk.  You could try file-based backups - and I would. We don't really know what the problem is. If it is the motherboard, then you'll need to borrow someone else's computer for this stuff.  BTW, you can run a desktop on a $50-raspberry Pi, if you are really stuck for cash.
I took the HDD out, connected (internally) to another laptop. Same problems. Can't do much.
I posted a screenshot on my previous comment.

By 'file-based backup', are we talking about copying and pasting?
If yes, that failed and didn't work.


> **TheFu said:**
> 
We zoomed in on the HDD being the issue based on the subject of this thread.  Did you happen to check the SMART data yet?  That is normally how people check that.  It could be just a bad cable too. SMART usually shows that as ECC errors and Read-Errors.

I posted screenshots earlier from 'Disk' program/application, unless you need me to follow a different path?

> **TheFu said:**
> 
Again - your laptop doesn't have USB ports?  You can put almost any storage HDD/SSD into a cheap external USB enclosure.  I've seen these for $9.  I have a number of them - all sorts.  I prefer the "Dock" type, which support 2 HDDs over 1 USB3 connection. Then I can load raw drives into the "dock" and gravity holds it in place. Works with 3.5 and 2.5 inch SATA drives.  They run as fast as the drive would internally (almost always), since the "dock" has an external power and USB3 bus speeds are faster than all but the fastest NVMe drives anyway.  Think I saw one of these dual Docks for $25 a few months ago during a sale.  That's USD.

No internal slot for yet another drive but it sure does have USB ports.
The main issue here is, I have no such things as you mentioned. Even if I order that online, it will take days to arrive. I don't go out usually unless it's urgent. If that is our one and only option, I must find where these things can be bought. 
I prefer to use whatever available I have here first.


> **TheFu said:**
> I'm not convinced the HDD is really the issue.  A cracked motherboard (physically cracked) can create short circuits.  
But, no one and nothing happened to the motherboard as far as I'm aware.

> **TheFu said:**
> 
**Story ... not important:**
I've seen this a few times over my career.  I once dropped my personal laptop about 8 inches from a low couch to the floor.  That system never booted again.  The motherboard power connection was harmed.  It was just over 1 yr old, so out of warranty.  At the time, my credit card doubled the warranty on purchases, so I just needed to provide an official estimate to fix the problem and they'd reimburse me.  It was a $850 laptop. They gave me $650, since it has been used over a year.  I shopped about for a replacement about 4 months - I have multiple computers and didn't need a laptop at the time.  This was in 2011 ... and I still have that replacement laptop today. It is on the 3rd HDD now and I use it almost every day. It hasn't moved from the location since about 2013 when I moved to a very light, 2lb, laptop.
It's important to me because you are sharing your stories with me. It means a lot, thank you so much.

---

### Post by TheFu on 2021-05-19
The key to file-based backups is running them BEFORE htey are needed and for them to be "versioned."  That means a cp isn't the best choice. Making a weekly "cp" backup means you need as much backup storage as 5-200x the source files.  That's not very efficient.  With a real backup tool, it is easy to have 90 days of versioned backups that uses 20-30% more storage than the original.  Also, each increment backup takes just a few minutes, so it isn't a big deal and you'll allow them to run more often.  For example, last night backups for 3 system here:

```
=== Time for Backups to regulus === 
StartTime 1621401303.00 (Wed May 19 01:15:03 2021)
EndTime 1621401497.20 (Wed May 19 01:18:17 2021)
ElapsedTime 194.20 (**3 minutes 14.20 seconds)**
TotalDestinationSizeChange 196530021 (187 MB)


=== Time for Backups to hadar === 
StartTime 1621402504.00 (Wed May 19 01:35:04 2021)
EndTime 1621403066.37 (Wed May 19 01:44:26 2021)
ElapsedTime 562.37 (**9 minutes 22.37 seconds)**
TotalDestinationSizeChange 81611277 (77.8 MB)


=== Time for Backups to romulus === 
StartTime 1621403127.00 (Wed May 19 01:45:27 2021)
EndTime 1621403261.35 (Wed May 19 01:47:41 2021)
ElapsedTime 134.35 (**2 minutes 14.35 seconds**)
TotalDestinationSizeChange 142401 (139 KB)
```

My backups are all automatic.  My laptop has been powered down the last few days, or I'd show it, but ... here are the backups for the last 90+ days:
```
        Time                       Size        Cumulative size
-----------------------------------------------------------------------------
Sun May 16 00:07:04 2021         24.5 GB           24.5 GB   (current mirror)
Sat May 15 00:07:03 2021         15.9 MB           24.5 GB
Fri May 14 00:07:03 2021         17.5 MB           24.6 GB
Wed May 12 00:07:04 2021         15.7 MB           24.6 GB
...
Wed Feb 17 00:07:03 2021         47.6 MB           29.5 GB
Tue Feb 16 00:07:03 2021         32.2 MB           29.6 GB
Mon Feb 15 00:07:04 2021         69.0 MB           29.6 GB
```

Basically, I backup 24.5G of data and all the daily versions of that data going back to Feb 15 only use 29.6G.  When you see this, doesn't it seem like a no-brainer choice to run daily, versioned, backups?  The trick, of course, is to pick the data/information to be backed up.  I can restore any files or directories or a complete set from any of those dates.  The last backup version looks like a mirror, so getting the latest copy of a file is just a cp .... or copy/paste in a GUI.  I've used rsync for restores. The backup tool I use doesn't use hidden file types or funky tools. It uses rsync + gzip + diff.  Standard tools, so if I really need the data, it is there. Of course, using the --restore-as-of {DATE} option for any older versions is much easier.

My backups for systems at home all go to a single, USB3 1.5TB HDD, sitting in a $20 Dock. Considering that a 2TB USB HDD is only $45 these days, seems like cheap insurance to me. I don't backup OSes, just the settings and config data to put that all back in about 30-45min for each system. If my 10 systems all died at the same time, it would be a bad day. 30min x 10 ... a full day, once replacement storage is installed. I'd certainly need to prioritize. So far, only 1 system has ever been impacted at a time the last 30 yrs.

Anyway, enough about that. It doesn't help today.

Temperature changes can cause lose connections on all electronics.  Stuff designed to work over wider temperatures uses larger connections, more solder.  Any little bump can make an iffy connection just lose enough to stop working.

For SMART data, I use **smartctl**. I don't trust "disks".  Plus, since I need to run smart testing weekly and long smart testing monthly on all the storage here, a GUI isn't exactly efficient.  If we know how to do things from the CLI/shell, then we don't have to re-re-re-relearn the new GUIs every 2-3 yrs.   But I'm not against all GUI tools.  gparted completely rocks!

As for trying to use stuff you already have, that's great unless it don't allow doing what is necessary.  Clearly, this has been unsolved for 6 days already, so the data really isn't that important.  

**Another story:**
One of my work systems (I was the project enterprise architect) was down for 6 hrs due to database corruption.  25K workers couldn't work. It cost the company about $50M in lost work and lost client implementation schedules. What's sad is that the system design would have made it a 10 minute outage with no more than 1 hour of data loss, had the client implemented that part. The client had already PAID for everything, but just didn't allow the hourly BCV snapshots to be setup, created, tested during a maintenance window. They always prioritized anything else higher - new features, other parts of the system, just not the BCV snapshots. We were 3 yrs into the implementation. Nearly every weekend, something new was being added - I think they didn't do changes when there were 5 huge holidays, but that was about it.  How'd you like to be the admin on that - every weekend - 11pm-6am, having to make system changes.  Glad I wasn't in operations.  The IT guys were great, but never really had any weekend off.
Even after the outage where it became clear who's fault it was, they still didn't prioritize doing it for over 3 months.  And rather than doing it all in 1 night, which was very possible, they decided to do it the way that caused the 3 full nights of effort and had almost as much risk.
This outage had visibility to the company leadership for a few weeks.

When you call that data recovery company, I hope they can help, but it won't be $200, unless nothing is really wrong with the hardware.  It is going to be expensive.

---

### Post by HermanAB on 2021-05-19
I've had a SSD fail after 2 weeks.  Since it was a brand new machine, I hadn't made any backups yet.  Grrr...

The new SSD is now 12 years old and I have a versioned backup system.

So, losing data due to no or incomplete backups, happens to everybody and the only way to avoid it, is through great diligence right from the start.  When you switch a machine on for the first time, you should put a backup method in place.

BTW, messing with partitions is almost a sure fire way to lose data.  Don't ever do that.  Plan the system properly and then leave the partitions alone.  If you really have a bad mix of partition sizes, then you can usually work around the issue with soft and hard links.

---

### Post by TheFu on 2021-05-19
> **HermanAB said:**
>  
So, losing data due to no or incomplete backups, happens to everybody and the only way to avoid it, is through great diligence right from the start.  When you switch a machine on for the first time, you should put a backup method in place.
 

Testify!  

Nobody is perfect.  I can admit that I've brought up 3 new systems the last few weeks and did not setup **any** backups for them at all.  

They are toy systems - a 21.04 desktop and (2) 21.04 servers.  The server installs were mainly to see the installation options, though I did put both into my LAN DNS, gave them carefully selected IPs, and pushed some ssh-keys over.
The 21.04 Gnome3 Desktop install has already been wiped. It was crazy bloated and using too much storage.

My VPN server doesn't have backups yet.  Since it doesn't have any data, just self-created certs, rebuilding it from scratch would take about 20 minutes, maximum. QR-codes make transferring client-side credentials much easier. 

But for my real systems, those that will have important data or important data processing, then having a basic backup very early in the deployment is important. All the backup scripts are nearly identical, with slight changes for hostnames, directories to be included, pre-backup and post-backup scripts to be run. Each is very similar, but not quite the same.

---

### Post by amjjawad on 2021-05-31
"Error fsyncing/closi 
ng /dev/sda1: Input/output error"

This is what GParted is showing.

I can't do anything!

Edit: I was on the Live USB of Ubuntu 20.04 LTS.

---

### Post by amjjawad on 2021-05-31
Update:

In BIOS

Hard Disk: [Not Detected]

---

### Post by TheFu on 2021-05-31
> "He's dead, Jim."

Hopefully, you got all the data off as suggested many times above before the failure. If not, you'll need to decide how much you are willing to pay for someone in the data recovery industry to replace the internal drive controller and attempt to restore it. Around here, that isn't hundreds of dollars, but thousands of dollars.

Perhaps the $40 for a cheap external USB backup disk seems like a bargain at this point.

You could still remove the drive, put it into a $20 USB disk enclosure, connect it to another system, and maybe gain access to the data.  Just depends on where the problem is - in the motherboard or in the disk or in the cabling that connects them. Each is bad, just in different ways.

---

### Post by amjjawad on 2021-06-03
Wait, how come it's dead and I still can see GRUB Menu?!

Yes, BIOS couldn't read it but when I boot normally, I can clearly see the GRUB Menu.

However, when I see (initramfs), no commands can be found, not even sudo!

---

### Post by TheFu on 2021-06-03
initramfs is a limited shell.  Only very specific commands are available.

As to the other question, IDK.

---

### Post by amjjawad on 2021-07-28
After nearly 2 months, I'm here to report that, the laptop is [still] doing crazy stuff.

I did a full test for each and every single part of the laptop.

I couldn't find out what is going on? 

I thought, after using an old Hard Disk Drive instead of the one that is full of [Bad Sectors] which, no matter what I did, I failed to retrieve one single byte; I thought the problem was the [HDD with bad sectors] but, guess what?

I'm running the laptop now for two days [WITHOUT] any HDD. I'm booting from a LiveUSB that has Ubuntu 20.04 LTS. 

I think, most likely, the problem [was] the Operating System, not the actual HDD itself.

The [exact same behavior] happened to the laptop with another HDD.

I thought, the 2nd HDD is going to die as well.

I did more than one test and there is not even one single bad sector whatsoever.

Same behavior:
Laptop Freezes.
I can't do anything unless turn it OFF from the [Power Button] and when I turn it ON again, well, [Freeze] again.

RAM test for 2 days = all good.
Laptop is running LiveUSB with Ubuntu 20.04 for 2 days = all good.

While I'm not an expert to confirm that the problem was the [OS] which was Ubuntu 18.04 but, at the same time, I can't think of any other cause. 

I can't blame the OS for damaging my HDD, which was [NEW] and I was using it super carefully. However, I can't think of any other cause!

The damage is done, period.

My HDD is full of bad sectors. I don't have thousands of dollars to try to pull the data out.

I've being using Ubuntu and its official variants since 2010, never ever seen the exact same problem.

The moment I started to use Ubuntu 18.04, I have faced many issues, to name the last, the one that I reported in this thread.

I feel bad and sad.

---

### Post by dragonfly41 on 2021-07-28
> My HDD is full of bad sectors. I don't have thousands of dollars to try to pull the data out.

If you are willing to gamble about $90 (I repeat, gamble) I have read that a very old app SpinRite at grc.com has provided HDD recovery for some enthusiasts. But only from what I have read.  I have not gambled myself on this product.

Perhaps post a message to the creator of SpinRite with a summary of the problem. A money back guarantee I would try.

[P.S.] Some further references to SpinRite [posted here]("https://community.spiceworks.com/topic/95954-how-many-bad-blocks-is-too-many").

[P.P.S] Further idea. Install R-Linux in your LiveUSB (which seems to work)
then [follow guide here to examine drives]("https://www.r-studio.com/free-linux-recovery-help/bad_sectors.html") with bad sectors.  The only problem with this idea is that installing apps into LiveUSB is not persistent and you will have to reinstall each time you boot up LiveUSB.  But it costs nothing to try.

[P.P.S] Referring to post #9 did you try without options?

(i.e., without -a or -p options)
ubuntu@ubuntu:~$

---

### Post by TheFu on 2021-07-28
I've had spinrite for decades.  It violates all sorts of "do no harm" requirements that data recovery experts follow.  It is also limited to 2TB, since it doesn't do GPT.

It has been about 15 yrs since I used spinrite.  It is basically like **ddrescue**, **badblocks** and normal versioned backups. If we do normal backups using tools that validate the source partition data can be read, then we've exercised the storage areas and provided the HDD drivers a chance to relocate any lazy bits.

Don't use spinrite on flash storage or SSDs.

---

### Post by dragonfly41 on 2021-07-28
O.K. ditch that idea .. although the author seems to know his stuff (but on old HDD's).

But R-Linux is risk free.

---

### Post by TheFu on 2021-07-28
Has the OP posted the system logs showing problems?  The last 3 weeks or so, my 18.04 VM host has had some stability issues.  I've narrowed it down to either the kernel line (not just 1 kernel) or bad RAM.

On my system, after a crash, I can see the stack trace in logs from the prior crashes using journalctl -b -2. The failures look like this:
```
Jul 26 23:43:05 hadar kernel: Hardware name: System manufacturer System Product Name/ROG STRIX B450-F 
Jul 26 23:43:05 hadar kernel: Call Trace:
Jul 26 23:43:05 hadar kernel:  dump_stack+0x6d/0x8b
Jul 26 23:43:05 hadar kernel:  bad_page+0xcb/0x120
Jul 26 23:43:05 hadar kernel:  free_pages_check_bad+0x5f/0x70
Jul 26 23:43:05 hadar kernel:  free_pcppages_bulk+0x472/0x6d0
Jul 26 23:43:05 hadar kernel:  ? page_counter_cancel+0x23/0x30
Jul 26 23:43:05 hadar kernel:  free_unref_page_commit+0xb9/0xe0
Jul 26 23:43:05 hadar kernel:  free_unref_page_list+0x108/0x190
Jul 26 23:43:05 hadar kernel:  shrink_page_list+0x379/0xbb0
Jul 26 23:43:05 hadar kernel:  shrink_inactive_list+0x204/0x3d0
Jul 26 23:43:05 hadar kernel:  shrink_node_memcg+0x3b4/0x820
Jul 26 23:43:05 hadar kernel:  shrink_node+0xb5/0x410
Jul 26 23:43:05 hadar kernel:  ? shrink_node+0xb5/0x410
Jul 26 23:43:05 hadar kernel:  balance_pgdat+0x293/0x5f0
Jul 26 23:43:05 hadar kernel:  kswapd+0x156/0x3c0
Jul 26 23:43:05 hadar kernel:  ? wait_woken+0x80/0x80
Jul 26 23:43:05 hadar kernel:  kthread+0x121/0x140
Jul 26 23:43:05 hadar kernel:  ? balance_pgdat+0x5f0/0x5f0
Jul 26 23:43:05 hadar kernel:  ? kthread_park+0x90/0x90
Jul 26 23:43:05 hadar kernel:  ret_from_fork+0x22/0x40
```

So, I wrote a tiny script to see how often the issue happens on each boot:
```
$ ~/bin/crashing 
Boot -0 : 1
Boot -1 : 5
Boot -2 : 8
Boot -3 : 1
Boot -4 : 93
Boot -5 : 223
Boot -6 : 596
Boot -7 : 258
Boot -8 : 383
Boot -9 : 0

```
0 or 1 means no problem.  Higher numbers show stack problems. Here's the script, but I doubt it will work for others as is:
$ more ~/bin/crashing
```
#!/bin/bash
for i in {0..9} ; do
   RC=$(journalctl -b -$i |grep  'dump_stack' |wc -l)
   echo "Boot -$i : $RC"
done;
```

3 boots ago, was when I lowered the DDR4 RAM speed from 2800 to 2733 and that ran without issue for about 10 days.  Then a few days ago, even at 2733Mhz, the system began crashing - full lockup. No different TTY or ssh was possible. Had to use the reset button.  Boot -2 and -1 where at the same 2733Mhz, but the last reboot I slowed the RAM again to 2666Mhz (I think).  
```
$ sudo inxi -m
Memory:    Used/Total: 15719.5/32108.7MB
           Array-1 capacity: 128 GB devices: 4 EC: None
           Device-1: DIMM_A1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-2: DIMM_A2 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-3: DIMM_B1 size: 8 GB speed: 2666 MT/s type: DDR4
           Device-4: DIMM_B2 size: 8 GB speed: 2666 MT/s type: DDR4
```

The box has been very busy the last few days. It has been up about 22 hrs now, which is good.  On Saturday, during a maintenance window, I'll reseat the RAM, swap some paired DIMMs around in the slots, put the speed back up to 2933Mhz and see if that helps. If not, I'll take 2 of the sticks out, since the machine as 2-pairs which weren't bought as a matched set.  16G is a little tight for this system, but if I'm careful on RAM use, it should not be an issue.  
```
$ free -m
              total        used        free      shared  buff/cache   available
Mem:          32108       15222        6836          41       10049       16382
Swap:          4355         119        4236
```
My current RAM use is just on the 16G cusp. I can half RAM allocated to one of the VMs and not power another, which should keep it around 12G used.  I can move one or two VMs to a different system too.

Should say, this VM host has been fairly stable for 2.5 yrs.  SMART data for the connected storage is all fine. No bad blocks or any reallocated blocks at all.  That was the first thing I checked.  Weekly SMART tests run automatically and get logged on all my storage.

---

### Post by amjjawad on 2021-08-05
Hi again,

> **TheFu said:**
> Has the OP posted the system logs showing problems?

1- No one has ever asked me to post any log of any kind AFAIK.
2- Even if that happened, I can't login to the system anyway.

---

