---
title: "Critical problem w/ deleted files not freeing up space,(Windows files under Ububuntu)"
date: 2007-11-12
forum: General Help
---

### Post by enthusaroo on 2007-11-12
I have a dual-boot system with both Windows XP and Ubuntu 7.10 installed. I've been using Ubuntu probably about 99% of the time for the last month or so. Under Windows I use the IFS Drives program to be able to read/write to the Linux partitions. Recently a guest visited and he asked to use Windows, so for security I set the drive letter on IFS Drives for my Ubuntu partitions to "[none]", because I wanted to keep my data on those partitions nearly invisible. I didn't want the guest to be able to easily click around and find those mounted drives.

Here is the problem... I forgot to set the drive letter under Windows after my friend left. While using Ubuntu, I deleted about 2gigs worth of avi file movies under Windows, and it seems to delete the files properly. I deleted them, because I was trying to free up some space. The problem though is when I checked the amount of free space under the Windows partition, it hadn't changed from the amount before the 2gig of files were deleted! The files are clearly gone, but yet it didn't free up any space! I logged into Windows, but the files are clearly not there. Plus, there's also nothing in the Recycle Bin. Therefore, it seems like these files are either floating around in space somewhere lost, or I don't know... How can I get my free space back? I'm down to only 300mbs free on my Windows partition, so when I deleted 2gigs of files I was expecting to have about 2.3gigs free.

Please help!! I'm not sure if this is because I had switched the drive letter off under IFS Drives, or perhaps it's an issue with Ubuntu?

I also tried defragmenting the Windows drive, but it didn't help with this particular problem..

---

### Post by seshomaru samma on 2007-11-13
I don't dual boot but I noticed that Ubuntu tends to create a its own hidden garbage folder on new drives. So it is quite likely that your deleted AVI files are hidden somewhere. If you are using nautilus, click ctrl+H to view hidden files (or just enable them through the 'view' menu) and delete them from the hidden folder.

---

### Post by enthusaroo on 2007-11-13
seshomaru samma: Thank you for your reply.

Unfortunately, I tried to view all hidden files, but I can not find the files that were "deleted". I have been through every option in Windows that I can think of, as well. The 2gigs of space that should have been freed up is just mysteriously "missing". :(

Any other ideas?

---

### Post by enthusaroo on 2007-11-13
Ah ha!

I just found it under:
/windows/.Trash-<username> using the Disk Usage Analyser tool. I hope this answer saves somebody some time. :p

---

