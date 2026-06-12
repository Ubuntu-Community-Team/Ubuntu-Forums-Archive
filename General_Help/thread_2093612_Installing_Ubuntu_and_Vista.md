---
title: "Installing Ubuntu and Vista"
date: 2012-12-11
forum: General Help
---

### Post by anon_private on 2012-12-11
Hi,

I am assuming that if I try to install Ubuntu I will have the option of replacing the Vista system, or installing Ubuntu alongside Vista.

A question.

To install Ubuntu alongside Vista must vista be a working OS?

At present, Vista does not work on my machine, but at a later date, I may try to get it working

Thanks.

A

---

### Post by offgridguy on 2012-12-11
> **anon_private said:**
> Hi,

I am assuming that if I try to install Ubuntu I will have the option of replacing the Vista system, or installing Ubuntu alongside Vista.

A question.

To install Ubuntu alongside Vista must vista be a working OS?

At present, Vista does not work on my machine, but at a later date, I may try to get it working

Thanks.

A
No it doesn't have to be working.  But do you have a hardware issue with your
machine that may affect another OS??

---

### Post by Bucky Ball on 2012-12-11
Vista does not need to be working. 

There is the 'Something Else' option at the partitioning section of the install which allows you to partition manually. You could then make an extended partition and put Ubuntu in that. You need a couple of partitions at least (in this case, logical drives inside the extended partition) for Ubuntu. A normal setup is three:

/ = where the OS goes, 15Gb fine;
/home = where your personal data goes, big as you like;
/swap = 2Gb fine at the end of the drive after /home.

The other option is a large / and /swap as per above. A /home directory will be automagically created in / for your personal documents. Downside of this is if you break the system and can't get in, you will need to back up your /home directory somehow before reinstalling (a last resort always). 

With a separate /home partition your personal data is theoretically safe and you can reinstall the OS to the / partition.

Hope that helps some.

PS: Using 'Something Else' you will clearly see your existing partitions as they will be NTFS or FAT. Ubuntu needs to use an EXT* partition; choose EXT4. The mount points /, /home and /swap are all defaults in the partitioning section (the app Gparted) which you can choose easily.

---

### Post by Impavidus on 2012-12-11
Keep in mind that if you get vista working again by reinstalling it may overwrite the bootloader, so that ubuntu seems to disappear. It's still present and using your ubuntu installation dvd/usb you can repair it, but if you think you need to reinstall vista the preferred order is to reinstall windows first and then install ubuntu.

---

### Post by Bucky Ball on 2012-12-11
> **impavidus said:**
> ... If you think you need to reinstall vista the preferred order is to reinstall windows first and then install ubuntu.

+1.

---

### Post by anon_private on 2012-12-12
Thanks to all.

Very helpful.

Happy Christmas

A

---

### Post by Bucky Ball on 2012-12-14
And a happy xmas to you. ;)

Please mark thread as solved from Thread Tools at top right of this page when you are satisfied it is.

---

### Post by offgridguy on 2012-12-15
> **Bucky Ball said:**
> Vista does not need to be working. 

There is the 'Something Else' option at the partitioning section of the install which allows you to partition manually. You could then make an extended partition and put Ubuntu in that. You need a couple of partitions at least (in this case, logical drives inside the extended partition) for Ubuntu. A normal setup is three:

/ = where the OS goes, 15Gb fine;
/home = where your personal data goes, big as you like;
/swap = 2Gb fine at the end of the drive after /home.

The other option is a large / and /swap as per above. A /home directory will be automagically created in / for your personal documents. Downside of this is if you break the system and can't get in, you will need to back up your /home directory somehow before reinstalling (a last resort always). 

With a separate /home partition your personal data is theoretically safe and you can reinstall the OS to the / partition.

Hope that helps some.

PS: Using 'Something Else' you will clearly see your existing partitions as they will be NTFS or FAT. Ubuntu needs to use an EXT* partition; choose EXT4. The mount points /, /home and /swap are all defaults in the partitioning section (the app Gparted) which you can choose easily.
Thank you ; Bucky Ball, this answers a question i wanted to ask.

---

