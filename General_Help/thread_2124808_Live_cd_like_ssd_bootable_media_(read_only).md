---
title: "Live cd like ssd bootable media (read only)"
date: 2013-03-12
forum: General Help
---

### Post by sriramin on 2013-03-12
I have to use ubuntu in a system with mysql and / or apache. Apache can be given up if i cannot achieve readonly bootable disk feature. But mySql is needed. Or any other database server. 
I have to set up  a system which has to run unattended. The following are the criteria / conditions
1. The system might face improper shutdowns  due to power outage (frequent)
2. Very little clean up / maintenance will be done. Need to run 24 / 7 365 days.
3. Some custom scripts / programs will be developed

Now with the frequent improper shutdowns, the linux installation get corrupt. As such I need to have a read only bootable linux system with a separate disk / partition which can be read write . In this way improper shutdowns will not affect the bootable part. For the readonly part, I can use an SSD too. A second disk (SATA hdd) can be used to store the mysql data.  The HDD will have 2 partitions with the second partition to contain the backup of the first (mysql data backup). 
In case of any failure, a method to restore the ssd from an image.
Is this possible and if so how can this be done.

---

### Post by Cheesemill on 2013-03-12
Why not just buy a UPS?

This will keep your system running during short outages, but also instruct your machine to do a clean shutdown when the UPS battery is about to run out.

---

### Post by sriramin on 2013-03-12
Hi Cheesemill
Thanks for the cheesy reply. That is an option still available and will do so. Most of the UPS come with a RS 232 feedback and todays boards donot have rs 232. The only available will be used for my own application. How about using unionfs , ausfs

---

### Post by Cheesemill on 2013-03-13
Most modern UPS's come with a USB connection, at least all the ones I've sourced at work do.

---

