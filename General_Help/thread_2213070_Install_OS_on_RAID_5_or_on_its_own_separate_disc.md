---
title: "Install OS on RAID 5 or on its own separate disc"
date: 2014-03-24
forum: General Help
---

### Post by Tony_Lillie on 2014-03-24
I am putting together an Ubuntu 12.04 file server with a software Raid 5 (16tb with 12tb usable). Obviously there will be much data and it is important business data. My question concerns the location of of the OS. Should I install the OS on the RAID 5 or put it on a small separate disk?

Obviously putting it on the array will keep it "safe" with the array being able to lose 1 disk, but if something unexpected happens to the OS then it's tied to the rest of the data on the array and that's potentially complicated. Though, I guess I could create a separate partition for the OS within the array, it still feels potentially risky having the OS on the same disks as the data.

If the OS is on a separate disk, I can image that disk easily and though it will not have the "safety" of the RAID 5, if the OS disk dies I can just install a new one and drop an image onto it. If that happened would there be any issues, like the array being unreadable or unmountable or "insert catastrophe here"?

Thoughts anyone?

---

### Post by TheFu on 2014-03-24
This is all opinion.

Funny things happen when RAID fails or degrades, especially with RAID5. It is much nicer to have the OS mirrored manually and easily bootable as needed on either device.  

I would
* Create 2 small partitions on 2 different disks for the OS, apps, settings. Manually mirror the partition as needed.
* Connect up the RAID storage - for data only
* Setup 100% bulletproof backups for the OS, Apps, Data, settings.  Last month a friend was called to a client with RAID, but ZERO backups. RAID never replaces backups, especially if the data is critical. That client lost everything.

There are always reasons to go in a different direction. Often there are good reasons to do something different.

---

### Post by Tony_Lillie on 2014-03-24
What do you mean by "manually mirror"? That sounds different than RAID 1 which is what I was considering for the OS.

I coincide with your opinion on backups. People often fail to realize that an array (other than RAID 1) is actually more fragile than a single disk. Nothing replaces a solid system image...NOTHING!

---

### Post by TheFu on 2014-03-24
Good to hear.
Actually, RAID1 can be fragile too - different paths to the bytes being written means a chance for differences. RAID1 is the fastest way I know to write corrupt data (for whatever reason) to 2 disks ... besides RAID10. ;)

Manual means '**dd**' the first time, then **rsync** as-needed later, probably 2-7 days after any system updates.  This exact method has saved my **** a few times.  Backups could too, but most backups were not easy to restore in the old days when people did the monthly/weekly fulls and daily incremental backup schedule stuff.  These days I use modern backup tools that have the most recent backup as a mirror (like rsync) and any older backups are diffs from that.  No more fancy backup schedule needed.

---

### Post by Tony_Lillie on 2014-03-25
A couple more issues...

Do I need a swap partition on the RAID 5 now that I know I am not installing an OS to it?

Can you guide me to some decent posts or tutorials on setting up the RAID 5 during install? Everything I've found thus far is aimed at those who are installing an OS on the array. I'm not doing that, but would like to set up all the disks with the install interface because I find it to be very user friendly. Can I do both things at once with the installation interface? 
 
I've been experimenting with some spare equipment and keep getting stuck on the "mount point". Where should I mount the array?

---

### Post by TheFu on 2014-03-25
I've never attempted to setup RAID during an install. It is pretty easy post install anyway. Lots of guides for that.

You can mount the array ANYWHERE YOU LIKE. Put it where it makes sense. There are a few limitations on where you can put the array, but these aren't really limits - just common sense.
* onto a directory that is always available during mounting - so if you mount a file system onto another external disk that is mounted after boot (not during bootup), then the directory needs to already be there.
* filename and directory name limits apply - if you don't put the mount point too deep, this should never matter. I think 4096 is the current character limitation for most systems. When it was only 512, I did run into a few issues at work - so we had to rebuild the kernel with higher limits and rebuild a commercial DB.
* Avoid weird characters in the directory/filenames. 

See, this is normal stuff.

Depending on the purpose of the data on the array, that would determine where I would mount it.  Are you using LVM to make storage management more flexible?

---

### Post by Tony_Lillie on 2014-03-25
Thank you for your help. Yes, I will be implementing LVM (snapshots are soooo nice). Do I need a swap partition on the array?

---

### Post by TheFu on 2014-03-25
What are the pros/cons to putting swap on an array? What is the purpose of swap? Does it make sense to use an RAID for swap?

---

### Post by Tony_Lillie on 2014-03-25
I'm guessing you are trying to get me to find my own answer. So... my limited knowledge tells me that swap is for the OS, so I doubt it's useful on the array. Plus I have a ton of RAM, so swap will see little use anyway. So, I'm going with no.

How did I do?

---

### Post by TheFu on 2014-03-26
There are valid reasons to and not to put swap in the array. Your list is a little short, but if you are happy, then that's all that matters.

What matters is that you've considered the pros/cons for the solution decided and think it makes sense.

I wouldn't. Seems like a lot of complexity for something that is supposed to be fast, and shouldn't hold anything very long.

---

### Post by Tony_Lillie on 2014-03-26
I'm learning... but really enjoying it! You have been most helpful. Thank you!

---

