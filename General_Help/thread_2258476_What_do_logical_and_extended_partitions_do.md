---
title: "What do logical and extended partitions do?"
date: 2014-12-28
forum: General Help
---

### Post by John_Combe on 2014-12-28
I am confused by what the logical and extended partitions that can be created in GParted actually do. I have read that only four primary partitions can exist on a hard drive at once and that is rather limiting when trying to run multiple operating systems from one hard drive, and to get around that logical and extended partitions are created and used. I decided which two types of Linux I want to install but in order to do so I need to understand what logical and extended partitions are and how they function. 
Supposedly I could install the two types of Linux by creating 2 / partitions (primary) and 2 /home partitions (primary) followed then by a swap partition in the extended format, which is supposed to be able to be used by either Linux without causing any conflicts.
If the above can be done I still would not know what logical and extended partitions are and how they function, something that really bothers me. Practical examples of logical and extended partition use along with reasons for them would help bridge the gap between reading about them and using them.

---

### Post by Bucky Ball on 2014-12-28
Example: One disk. Create an extended partition which uses all the space on the one disk. Inside that, you can put as many logical partitions as you like (theoretically). If you have three partitions on a drive and then create an extended partition with the remaining space, you can create as many logical partitions as you like inside the extended partition. The system will see that as four partitions, three primary and one extended, but the extended can have however many logical partitions as you like. 

An extended partition is a bit like a container. You fill it with logical partitions, but the extended is considered to be one partition, regardless of how many logical partitions are contained within it.

Hope that helps. The attached screenshot of my Gparted should give you the idea. Notice that sda3 is an extended partiton with a heap of logicals inside that. As long as primary's and an extended equates to four, you are good to go. ;)

---

### Post by grahammechanical on 2014-12-28
It should be noted that this matter of a 4 Primary partition limit and the need for an Extended partition with Logical partitions inside is only applicable to motherboards with a BIOS boot system. Most motherboards use the UEFI boot system with GPT. 

Wikipedia gives a better explanation that I can. Wikipedia and Ubuntu wiki is where I get my knowledge from.

> [COLOR=#000000]Supposedly I could install the two types of Linux by creating 2 / partitions (primary) and 2 /home partitions (primary) followed then by a swap partition in the extended format, [/COLOR]

No you can't. You would be trying to exceed the 4 Primary partition limit. The Extended partition is a special kind of primary partition. The Extended partition has to be one of the four partitions. Installing Linux on some machines with a BIOS boot system is made more complicated because the manufacturer and Microsoft use the full number of primary partitions.

A default install on Ubuntu on a blank hard drive in BIOS boot system machine would use 2 primary partitions. The first primary partition for Ubuntu and the second primary partition as an Extended partition inside of which would be a logical partition for swap.

Regards.

---

### Post by Dennis N on 2014-12-28
You can make a GPT partition table with either BIOS or UEFI systems, and can dispense entirely with the need for an extended partition and logical partitions. With a GPT partition table, all partitions are primary partitions.

---

### Post by ajgreeny on 2014-12-28
Just bear in mind that if using MBR/BIOS and not UEFI, Windows **MUST** have a primary partition; it is not as clever as Linux as it can not boot from a logical partition, so if you tried to follow Bucky-Ball's first example and make all of a disk into an extended partition filled with logical partitions, you would be unable to boot Windows from that disk.

---

### Post by Sef on 2014-12-28
Best to put Windows on the first primary partition.

---

### Post by oldfred on 2014-12-28
If not ever installing Windows on a drive, you can use gpt with Linux whether UEFI or BIOS booting. Then you do not have the primary, extended and logical partition issue.

If system is BIOS, and you do use gpt, you must create a tiny 1 or 2MB unformatted partition with the bios_grub flag is using gparted. Grub does not correctly install without the bios_grub partition as a place to store core.img.

I have used gpt with my BIOS system since 10.10 without any real issue. My XP on another drive would not read the gpt drive, but I had not any NTFS partitions on drive anyway. Newer Windows on another MBR drive will read a NTFS partition on a gpt drive, but Windows only boots with UEFI from gpt partitioning.

There is a soft limit of only 128 partitions with gpt, and they all are in effect primary. You can modify partition table for more than 128 entries but I have not seen it done nor know how.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

