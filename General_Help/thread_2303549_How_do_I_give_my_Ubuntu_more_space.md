---
title: "How do I give my Ubuntu more space?"
date: 2015-11-19
forum: General Help
---

### Post by Mihin_Sumaria on 2015-11-19
I recently installed **Ubuntu 15.10** along side my Windows, so I basically dual booted the system. I was not sure how I would feel about Ubuntu, so I gave it only 17 GB space. Now I want to give it an **additional space of 100 GB**, how do I do so?
I have installed gparted on my system, and burned it's iso onto my usb (LiveUSB). I tried figuring out how to do it by myself by referring to other threads in this forum, but I did not really understand how to go about it. In the other threads they keep mentioning a partition 'extended' which would be present along side the other partitions after one dual boots their system. But I could not find any such partition. This is a screenshot of my gparted: 

[IMG]http://s21.postimg.org/tydop59lz/gpartedss.png[/IMG]

Apart from this can the 'Extend Partition' option in Windows 10 Disk Management utility do the job? The shrink volume button in the shrink volume dialogue box is greyed out for windows. But I can resize my partition in gparted. 
Please give me a step by step procedure of how to go about it. Thanks!

---

### Post by grahammechanical on 2015-11-19
The need for an Extended partition into which we can create Logical partitions is only appropriate to motherboards and disk drives that have msdos partition tables. If you have Windows 8 or Windows 10 pre-installed then you will have UEFI boot system and GPT partition table. The GPT partition table is part of the UEFI specification. But it is possible even with a BIOS boot system motherboard to have GPT partition table on the hard disk. I have done this.

It seems that you have GPT partition table. So, do not get confused by threads dealing with issues relating to BIOS boot system and msdos partition tables.

1) Use Windows utilities to defrag Windows and do it more than once and restart Windows each time.
2) Use Windows utilities to resize and move Windows partitions to create unallocated space and restart Windows.
3) Use Gparted running from a Ubuntu live session to expand the Ubuntu partition to take up the empty space. Gparted is part of the default applications in a Ubuntu live session. No need to install it on a live session.
4) The key symbol against the Ubuntu partition (sda8) and the swap partition (sda9) indicate that they are active partition and so are locked. Gparted in the live session will let you mark the swap partition to swap off. Then you can resize or move the Ubuntu partitions.

If you are going to resize (shrink) sda4 (ntfs) that will create unallocated space in from to sda8 which you can expand sda8 into. Job done.

If you are going to resize sda5 (ntfs) that will create unallocated space after sda9 the swap partition. So, you will then need to move sda9 so that the unallocated space is in front of sda9 but behind sda8. Then you can expand sda8 into the unallocated space.

Pictures

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Oh, have a means of restoring Windows and back up your data.

Regards.

---

### Post by Mihin_Sumaria on 2015-11-19
Thank you! I'll send updates regarding the same.

---

### Post by Mihin_Sumaria on 2015-11-20
Thanks a lot! It worked!

---

### Post by Bucky Ball on 2015-11-20
Great news. Please see the first link in my signature. Thanks and enjoy. :)

---

