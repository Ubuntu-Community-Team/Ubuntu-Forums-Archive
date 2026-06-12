---
title: "External USB drive becoming read only."
date: 2021-04-17
forum: General Help
---

### Post by rsteinmetz70112 on 2021-04-17
I have an external USB drive I am using to keep an archive of my network.

I have the drive listed in the fstab and on boot it mounts but at some point it remounts as read only. 
unmounting and remounting makes it reed write again.

This is the line in fstab.
```
UUID="8beb703e-d3f8-4f39-a97c-b27b8f9c9875" /backup ext4 rw,noatime,errors=remount-ro 0 1
```
I'm not sure how I arrived at this particular combination.
The drive is usually /dev/sdf

Checking the logs the drive seems to be overheating so I moved it to a better ventilated location, maybe that will help or maybe It's getting ready to fail.

---

### Post by TheFu on 2021-04-18
> **rsteinmetz70112 said:**
> maybe It's getting ready to fail.
^^^^^^^^^^^ This.  All storage is going to fail. We don't get to pick when. Sometimes it fails on day 2 and sometimes it fails after 15 yrs. Often, drives provide hints that something is wrong, but not always.  Backup storage fails too, but hopefully not at the same time that primary storage fails.  That's our gamble every time we make copies to different storage for backup reasons. I bet someone in the world had both their primary storage AND their backup storage fail on the same day.  Thankfully, the stars, moon, and Earth have never aligned that way for me. ;)  So far.

Assuming you've done all the other drive troubleshooting stuff already.  If you have data only on that drive, then it isn't a backup. It is primary storage.  **Backups have at least 3 copies.**
[LIST=1]
[*]Primary storage
[*]Local copy
[*]Remote copy
[/LIST]

My Mom had a "backup" disk. It was an external USB drive.  One day I wasn't really watching her, but was paying just enough attention to catch her, talking to herself about the process.
a) Backup to the backup drive.
b) delete from the "hard drive" - her name for the internal computer.
c) Now it is "backed up."
She honestly though that because the name of the external drive was "backup", that was something special, magical.  I explained that she couldn't delete the original file from the internal hard drive. At least 2 copies were needed. I also explained that I only pulled selected files from her "backup" HDD to my storage (3-states away) once a week, so until Friday night, she would have 1 copy and she needed 3 copies for a proper backup.

I fear this is a common mistake by non-technical people.

I renamed the drive from "backup" to "2nd-copy" and moved the mount from /Backups to /2nd-copy ... to make it clearer.

If you have stuff you'd like for long term archival, perhaps using a 50+ yr BluRay disc would be advised?  There's a special type of disc and writer needed for these 50+ yr storage media. Sorry that I cannot recall the correct name now.  I used to backup data to 1S and 2L DVDs for about 5 yrs. At the time, DVD media storage was much cheaper than spinning disks.  

It is about 15 yrs since the last data was written to those DVDs.  Over time, some bits have been lost. Fortunately, the media is still readable and I added 10% par2 parity files beyond the parity that the disc media writer automatically added. A few times, I've needed to use those par2 files to recover files.
[https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2](https://blog.jdpfu.com/2011/06/12/optical-data-recovery-technique-with-ddrescue-and-par2) has an example.

It has been at least a few years since I pulled data off the optical media, so I'm doubtful that ddrescue and par2 can retrieve it now. Hopefully, I'll never need to find out. Most of the important data was long ago put onto spinning disks for greater convenience and gets mirrored to other storage, but not all of it has made it off the discs yet.

---

### Post by kurt18947 on 2021-04-18
> If you have stuff you'd like for long term archival, perhaps using a 50+  yr BluRay disc would be advised?  There's a special type of disc and  writer needed for these 50+ yr storage media. Sorry that I cannot recall  the correct name now.


You're thinking of M-Disc probably. 25 & 50 GB.capacities and yes they do require a burner rated for them. There are archival DVDs that are supposed to be longer lived than those found at Big Box stores. Here's an example of archival DVDs

[https://www.amazon.com/50-Pak-MAM-Mitsui-Inkjet-ARCHIVAL/dp/B08NQ81FFX/ref=sr_1_7?crid=2BJA1AK8O0X4U&dchild=1&keywords=archival+dvd&qid=1618784096&sprefix=archival+DVD%2Caps%2C151&sr=8-7](https://www.amazon.com/50-Pak-MAM-Mitsui-Inkjet-ARCHIVAL/dp/B08NQ81FFX/ref=sr_1_7?crid=2BJA1AK8O0X4U&dchild=1&keywords=archival+dvd&qid=1618784096&sprefix=archival+DVD%2Caps%2C151&sr=8-7)

---

### Post by TheFu on 2021-04-18
Thanks kurt18947, m-disc is it. The m-disc drives do work with normal DVDs and blurays too, I understand, so they aren't 1-trick tools.

---

### Post by rsteinmetz70112 on 2021-04-25
After relocating the drive it continued to have problems.
I replaced the drive with a new one. 
So far so good. Still getting everything back on it.
I'm going to mark this solved.

---

