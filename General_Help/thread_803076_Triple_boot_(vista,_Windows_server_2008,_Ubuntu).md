---
title: "Triple boot (vista, Windows server 2008, Ubuntu)"
date: 2008-05-22
forum: General Help
---

### Post by drewtown on 2008-05-22
I was wondering if anyone had any tips for this. I'm guessing I need to install Vista->WS 2008->Ubuntu.  Please let me know what you think.

Drew

---

### Post by yaknowwat on 2008-05-22
What are the system Speculations you will be doing this on?

This matters a lot on the approach and technique you should use.

---

### Post by drewtown on 2008-05-22
This is going to be a custom built system here are the spec.

Intel Core 2 Duo 3.0GHz 45nm
4 GHz Ram
Asus p5e mobo
Seagate 750GB hdd
Corsair PSU, 600ish Watts
Nvidia 512mb pci-e 2.0 8800GT graphics card.

This is a clean system so far with nothing on it.

---

### Post by drewtown on 2008-05-22
shameless bump.

---

### Post by cdtech on 2008-05-22
all on one drive?

Sure, Window's first....

Might as well throw Ubuntu Server Edition on there as well..

---

### Post by drewtown on 2008-05-22
I don't see it being ridiculous, you see sites all the time showing how to do XP, Vista, and Ubuntu, or Mac, Vista, and Ubuntu.

---

### Post by yaknowwat on 2008-05-22
The issue is the amount of Partitions a Hard Drive can handle the Max is 4 main Partitions.

Personally I would Suggest Putting Vista in a Virtual Machine because Windows Server 2008 can do everything Vista can and has all the special effects as an optional addition from what i know.

Personal Suggestion :

Partition 1 - Windows Server 2k8
Partition 2 - Linux
Partition 3 - Dedicated OS Sharing Partition (place the Vista Virtual Machine into this partition s you can run the Virtual Machine of Vista in both Windows Server and Ubuntu Linux) This can also be used to share files easily between Windows Server and Linux because Windows cannot stably read Linux Partitions.
Partition 4 - Logical - Swap

Partition Format Structure for the Suggested Setup:
1 - Primary - NTFS (200 GiB)
2 - Primary - Ext3 (150 GiB)
3 - Primary - FAT32 or NTFS (390 GiB)
4 - Logical - Swap (10 GiB)


If you really want your Original Design.

Your Purposed Setup:
Partition 1 - Windows Server 2k8
Partition 2 - Vista
Partition 3 - Ubuntu Linux
Partition 4 - Logical - Swap and OS Share

Partition Format Structure for the Purposed Setup:
1 - NTFS (150 GiB)
2 - NTFS (150 GiB)
3 - Ext3 (100 GiB)
4 - Logical (350 GiB)
~~(4) Swap (10 GiB)
~~(4) NTFS or FAT32 (340 GiB)


Then afterwards you setup Grub to have an option for booting to each OS.

That setup wont be to hard and the Ubuntu Install may automatically set it up.

I was sleeping and getting thing ready for Summer classes so i didn't reply ealier.

---

### Post by lswest on 2008-05-22
i'd say the order is fine, and if you set up the partitions right, everything should be fine.  (major problem would be if you did vista-->XP-->Ubuntu as XP uses an out of date windows bootloader that cannot start Vista, but since WS 2008 and Vista run the same version, it shouldn't be a problem)

---

