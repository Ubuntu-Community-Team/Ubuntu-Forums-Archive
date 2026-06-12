---
title: "Creating home directory"
date: 2007-07-01
forum: General Help
---

### Post by bilbobagins on 2007-07-01
Hi  I need to create a home directory for the o/s and related files to sit.I have been following he Psycocats site instructions but when I`m creating the new partition gparted only wants to make it a Primary, and not a Logical partition as shown in the sites how to... What am i doing wrong or is it ok. confused BILBO:(

---

### Post by orb9220 on 2007-07-01
You need to give more info on partitions. Like is windows installed too?

And why do you not want gpart to make a primary partition? You can have up to four per hardrive.

I have four which are winXP, / (root) , /HOME , ntfs Data partitions.

---

### Post by bilbobagins on 2007-07-01
OH no Windows dont exist on this machine
Partitions,,/dev/sda1 ext3 147.5 GiB used 20 GiB unused 120.2Gib
                /dev/sda2 extended 5.8GiB
                /dev/sda5  swap     5.8GiB
 I want to resize /dev/sda1, make a /home and move the O/S to the home partition,so that when upgrades to ubuntu it dont afect my own files.
I will try Psycocats instructions again .. now you put me right on primary partitions.
                            Jon

---

