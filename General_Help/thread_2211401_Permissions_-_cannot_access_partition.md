---
title: "Permissions - cannot access partition"
date: 2014-03-15
forum: General Help
---

### Post by rob-bob-dave on 2014-03-15
After installing Ubuntu, I decided to partition the drive. Using Gparted, I shrank the os partition and then created another partition for files and such. Unfortunately, I am not able to access the second partition. I have attempted to change the permissions to correct this, but this has been ineffective. I can change the permissions in /dev but after mounting the partition it, has the original privilages. I also created four partitions on a second drive (sdb) with Gparted which have no restrictions for reading and writing files.
sda1 is my os and apps partition, sda2 is the extended partition, sda5 is the swap partition, sda3 is the partition I cannot access.

The results for ls -l /dev/ are;

brw-rw----  1 root disk      8,   0 Mar 15 17:45 sda
brw-rw----  1 root disk      8,   1 Mar 15 17:13 sda1
brw-rw----  1 root disk      8,   2 Mar 15 17:45 sda2
brw-rw-rw-  1 root disk      8,   3 Mar 15 17:38 sda3
brw-rw----  1 root disk      8,   5 Mar 15 17:13 sda5
brw-rw----  1 root disk      8,  16 Mar 15 17:45 sdb
brw-rw----  1 root disk      8,  17 Mar 15 17:45 sdb1
brw-rw----  1 root disk      8,  18 Mar 15 17:13 sdb2
brw-rw----  1 root disk      8,  19 Mar 15 17:45 sdb3
brw-rw----  1 root disk      8,  20 Mar 15 17:45 sdb4

Is there another file that needs to be altered in order for the permissions to take effect?

---

### Post by coldcritter64 on 2014-03-15
> **rob-bob-dave said:**
> ....

Is there another file that needs to be altered in order for the permissions to take effect?
For mounting partitions at startup, and to set mount options the file to look into is /etc/fstab.

Some information for you on /etc/fstab : [[COLOR=#000080]--click here--[/COLOR]]("https://help.ubuntu.com/community/Fstab") 

Can you see your partitions listed in a nautilus window ? If so you can mount them manually every time by clicking on them in Nautilus or you can set them up in fstab for automounting.

I would not recommend altering the permissions of any system file (like those in /dev) in Linux, it is often a very good way to get your system into a very big mess.

---

