---
title: "best shared-partition filesystem?"
date: 2007-05-13
forum: General Help
---

### Post by leptogenesis on 2007-05-13
I've recently triple-booted with Ubuntu, Solaris, and Windows, and now I'm trying to decide what filesystem I should use to store the data I want to share between the 3 OS's.  I suppose I should note that I plan to use the 3 OS's approximately the same amount.  

Here's what I know so far:

FAT32: Can't use it because it has issues with filenames that are all uppercase.

ntfs: Obviously works with Windows; Solaris has software but I'm not sure how well it works; linux has pretty good read support.  Anyone know how well linux can write it?

ext2/ext3: Obviously works with linux; Solaris has software but I'm not sure how well it works; Windows has 3rd party software that works reasonably well.

ufs: Obviously works with Solaris; linux has software with "experimental" write support; I don't know of any Windows software for this.

So i guess the question is, what filesystems would you trust Ubuntu to write your data on to?

---

### Post by Happy_Man on 2007-05-13
I would go for either ntfs or ext3. Both of those have great read/write support in Windows and Linux, and for Ubuntu, there's a program called ntfs-3g in the repos that allows write access in linux. Try that out!

---

### Post by evolving_monkey on 2007-05-14
How large can a partition be in the ext3 format? I have about 80gigs I would like to share between Windows XP and Ubuntu and I would rather use something both support. I have heard some have problems with ntfs-3g. I am not sure if ntfs-3g for ntfs is reliable enough. Still trying it out.

Also do you have the same upper case filename problem as with fat32?

Thanks for your time.

---

### Post by imon9 on 2007-05-14
ext3 is my current choice..

tried ntfs, i suppose it not so good yet with ntfs-3g....

in windows use the driver ext2 IFS at [http://www.fs-driver.org/](http://www.fs-driver.org/)
this one is not oepn source driver for windows but it fixed-mount the drive so u dont have to manually mount it everything like the other program (ext2fs=open source) 

well..thereare ros and cons about the driver. It is just my opinion... ext2 IFS has not been updated for quite some time now..but it is still more stable...

---

### Post by LaRoza on 2007-05-14
FAT32 would be good if you want it to work immediately. What problems are you having with filenames? I've never had such problems.

FAT32 supports up to 2 Terabytes.

---

### Post by leptogenesis on 2007-05-14
> **LaRoza said:**
> FAT32 would be good if you want it to work immediately. What problems are you having with filenames? I've never had such problems.

I'm working with the [war]("http://en.wikipedia.org/wiki/WAR_%28file_format%29") structure for web applications...one of the directories in such a structure must be called "WEB-INF".  When I use ubuntu with it, the folder gets renamed (or at least interpreted as) "web-inf", which breaks the whole application.  Interestingly enough Windows doesn't have this problem...on ubuntu I'll create an upper-case directory name, cd out of the parent directory, and when I go back into the parent directory, the directory will be renamed to lower case.  Then I boot into windows, enter the same parent directory, and windows will interpret the file name as upper case.  I'm pretty sure that fat32 was supposed to have case-insensitive file names...so Microsoft isn't following its own standards.  Maybe Ubuntu shouldn't either...

Well whatever.  I think it's time to upgrade to a newer filesystem anyway.

---

### Post by leptogenesis on 2007-05-17
I guess I was wrong - if you mount the fat32 partition with the option "shortname=winnt", the names are interpreted properly and the web application is no longer broken (I wonder why this isn't the default...).  So I'm going with fat32.

Thanks for the help, everyone.

---

