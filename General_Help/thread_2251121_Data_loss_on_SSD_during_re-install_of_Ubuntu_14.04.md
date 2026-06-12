---
title: "Data loss on SSD during re-install of Ubuntu 14.04 64bit"
date: 2014-11-02
forum: General Help
---

### Post by robert48 on 2014-11-02
Hello

I have just shot myself in both feet. I have a system with two SSD drives, one I use for Ubuntu system (sda) the other for /home (sdb). I thought this would be a neat way to preserve my data. 

However the system played up and would not update so I re-installed. I used 'something else' to set it up, told it to reformat and install Ubuntu on sda mounted as root. I told it to mount sdb as /home, confirmed as ext4 file system, did NOT tell it to format and away it went. When I rebooted after set up all looked good, sdb was indeed the /home drive but....there were just the default files in the home/user directory and not the years of data acquired as expected.

This method of re-install with /home on another drive has served me well for years. So much so that my backups have been disregarded (big no no I know). I have tried ddrescue to create an image file to work on but TestDisk(v6.14) can't recover anything.

Any ideas on how best to work on an SSD with a view to recovering deleted files?

---

### Post by flaymond on 2014-11-02
Ubuntu got disk image writer (auto installed)....firstly...you must view your drive using that....check IF the data still there...please reply back....i will try to guide you..(maybe my beans only 8, but I will try to guide you with details and why so you can make sure you will never 'lost data' again). :D

---

### Post by robert48 on 2014-11-02
Hi, thanks for responding. Can you take this step by step please. The SSD drive can be mounted, the files I expect to see there are not present. How should I look at the drive?

---

### Post by flaymond on 2014-11-03
i think you need to reformat your drive back...the data still there..you just can't viewthem because the drive became 100% bootable drive...Using the same Image Writer...try format back...but dont overwritten it....because IF your file still there..and you overwritten it...and it will be lost....now..your drive is Hidden NSTF....you need to reformat your drive to be your 'old' USB back...

---

### Post by tgalati4 on 2014-11-03
*Testdisk* only tries to recover the partition and file/directory structure.  Use *photorec* (which is part of *testdisk*) to recover individual files.  You will get lots of directories with 500 nameless files in each one.  It's up to you to figure out what is important.  Expect to spend some time on this.  How many GB of data was on /home?

---

### Post by oldfred on 2014-11-03
If your correctly enabled trim on your SSD, you may not have any data to recover.

The purpose of trim is to erase blocks in advance, so when you write new data it does not have to do both erase & write. Typical hard drive just flags space as available and overwrites it, so old data is still there until overwritten.

Or with SSD backup is even more important.

Bit more info:
[http://www.techspot.com/news/52835-understanding-ssds-the-need-for-trim-overprovisioning-and-more.html](http://www.techspot.com/news/52835-understanding-ssds-the-need-for-trim-overprovisioning-and-more.html)

---

### Post by robert48 on 2014-11-15
Thanks for all of the responses. Your links were illuminating oldfred but I am still at a loss as to how I set up Ubuntu as a fresh install on one SSD and then use an existing 'Home' SSD without wiping the 'Home' data. As this is now my primary concern, data having been lost before as above, i have started a new thread. [http://ubuntuforums.org/showthread.php?t=2252912](http://ubuntuforums.org/showthread.php?t=2252912)

---

