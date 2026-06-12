---
title: "partitioning ubuntu 12.04"
date: 2012-12-21
forum: General Help
---

### Post by Drenriza on 2012-12-21
Hey all.

Currently i'am trying to move away from Windows 7 and 100% to Ubuntu, with wine for the programs i cannot live without.

And i'am wondering the following.

When partitioning the disks, can you partition a fast usb drive to be the system /boot partition, and a slower 7200rpm HDD as the / (root) and /home partitions.

Then boot from the usb and mount / and /home locations?

Currently i have partitioned my system as such (single HDD)
/boot 200MB
/ 60GB
/home 258GB

If this is not a good way of partitioning ones HDD, what would be a better way?

Kind regards.

---

### Post by vanadium on 2012-12-21
I would not use an external, albeit fast, USB to boot the system. Suitable partitioning for desktop use:
15 GB for /
/home: rest minus swap
swap partition, somewhat more than the size of your RAM.

For desktop use, one single partition for system and home is even easier, the only drawback is that you need to copy your data back if you do a fresh install at some point in the future.

---

### Post by Pjotr123 on 2012-12-21
No need for such complications.... I advise a single root partition, not even a separate /home: 
[https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-](https://sites.google.com/site/easylinuxtipsproject/faq#TOC-Should-I-create-a-separate-home-partition-)
(item 15, right column).

The only separate partition that I find genuinely useful, is the swap. :)

....edit: vanadium was quicker.... :P

---

### Post by Mark Phelps on 2012-12-21
> **Drenriza said:**
>  with wine for the programs i cannot live without.

Don't know what you know about Wine, but it's not the miracle cure that some folks think.  It runs some Windows stuff well, some poorly, and a lot -- not at all.

You need to go to the WineHQ site, check the Application Compatibility Database, and enter the app and version you want to use.

If there is no rating, or if the rating is less than Gold, and you need to RELY on that app -- then installing it in Wine is going to be a waste of your time because the features you need to use, most likely are not going to work.

---

### Post by Drenriza on 2012-12-21
> Don't know what you know about Wine, but it's not the miracle cure that some folks think.

Did that before doing the Ubuntu install :)

---

### Post by sdowney717 on 2012-12-21
I always use a separate /home now when setting up.
It can limit the damage and angst when upgrading installing and otherwise messing up. the '/' for the system only needs about 5gb, I typically give it from 10 to 30gb depending on how big the drive. Swap I dont go over 4gb. Leave the rest for /home on a separate partition.

---

### Post by Pjotr123 on 2012-12-21
> **sdowney717 said:**
> I always use a separate /home now when setting up.
It can limit the damage and angst when upgrading installing and otherwise messing up. 
That's what external backups are meant for.... The only real security. On the same disk it's just false security...

---

### Post by sdowney717 on 2012-12-21
yes, I have backups. what it does is let me more easily do an upgrade to the next version of ubuntu. /home just stays where it is and only the file system changes.
Or in the past I have totally destroyed my install somehow, and then I had to figure a way to copy off my files. Reinstall and copy back.

---

### Post by Drenriza on 2012-12-21
> **Pjotr123 said:**
> That's what external backups are meant for.... The only real security. On the same disk it's just false security...

It gives "security" in the sense of, if your / or /boot partition breaks. You can easily access the /home partition with rw permissions and extract data.

---

### Post by vanadium on 2012-12-22
The reason I have a separate home is not security, but convenience. When upgrading, I like fresh installs. Before a reinstall, I move my old home. After the install, I can selectively and fast place my data and selected configuration (e.g. thunderbird) back from my old home. Considering nowadays one can keep entire photo and music collections on the computer, keeping these data on the drive saves a few hours.
I also redirect the temp folders from the root partition to the /home partition. With small home partitions, there is a risk that the partition gets filled by temporary data of applications, e.g. Audacity.

In any case, users should be thought that data security is only in maintaining up to data backup copies on removable media. It is the only stuff worthy of a backup: operating systems and software can be downloaded freely and in different flavours all over the net. A users personal data and pictures, once lost, are lost forever.

---

