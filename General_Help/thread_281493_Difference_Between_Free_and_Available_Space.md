---
title: "Difference Between Free and Available Space?"
date: 2006-10-21
forum: General Help
---

### Post by Druid Healer on 2006-10-21
I was looking under gnome system monitor, and I discovered one of my partitions had a difference between AVAILABLE space and FREE space. The difference is about 10 gigs. This is under the filesystems tab. The partition in question is an old ext3 gentoo root partition. Is there a reason for this? Whats the difference. If needed, I can attach a screenshot. It might be worth noting that there are two unmounted partitions on that hard drive, that amounts to about 4.256 gigs. An old boot and swap partition. 

Thank you for your time and help in advance!

---

### Post by AdamDunn on 2006-12-04
My friend ran into this same question, so I did some digging around in code. As it turns out, the amount of disk space listed under "Available" is the amount that is available to a non-superuser. The amount listed under "Free" is the amount that is available to a superuser.
It is always a good idea to have some amount of disk space set aside that a normal user cannot write to. This set-aside-superuser-only disk space is used for emergency things, like if a process should get out of hand in writing files. This emergency space helps prevent your system from becoming unstable should something start to go wrong.

---

### Post by bom28 on 2006-12-04
By default ext2/ext3 partiotions have 5% of disk space reserved for root, it's often a bit too much for big partitions, and not useful for non-root partitions.
You can change the percentage, by typing in a terminal : "sudo tune2fs -m PERCENTAGE /dev/PARTITIONDEVICE"
(replace PERCENTAGE by the percentage you want and PARTITIONDEVICE by the partition ou want to change eg :/dev/hda1)

---

### Post by pmreimer on 2007-02-05
I have a 40 gig partition, and i have 1.8 gig difference between free and available space.  This wasn't always the case however, it matched a month ago. Azureus could be the culprit, but i cannot figure out how to fix it.   It is not the difference between super user and regular user, I promise.  What is the problem with azureus, or is it Java?

---

