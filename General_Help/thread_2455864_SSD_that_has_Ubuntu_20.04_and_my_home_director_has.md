---
title: "SSD that has Ubuntu 20.04 and my home director has 2 odd paritions"
date: 2020-12-29
forum: General Help
---

### Post by Old Jimma on 2020-12-29
Hi Community:

I installed a new SSD to hold the 20.04 operating systm and my home directory.

When I installed 20.04, I took all of the default options and did not do any partitioning.

I examined that SSD today with the "disks" app and have attached the png image of disk's summary.

What is odd is the SSD is a 1TB SSD and there are 2 partitions:
[LIST]
[*]a 536MB FAT partition, and
[*]a 1000GB EXT4 partition.
[*]
[/LIST]

Should I have formated the entire SSD as EXT before installing 20.04?

Should I worry that there is some sort of weird software on that FAT partition?

Thanks,
Old JImma from the Old Country

---

### Post by Hagar Delest on 2020-12-29
Hi,

No attachment in your post.

---

### Post by #&amp;thj^% on 2020-12-29
Anything like this?

---

### Post by oldfred on 2020-12-29
Default install  is / (root).
But with UEFI systems, you have to have an ESP - efi system partition which is FAT32 formatted.

But with 1TB drive, often better to not have it all as /. The default use of just / was from back when drives were a lot smaller or dual boot where a lot of larger drive was Windows.
Many like to then split / and /home and/or separte data partition(s).

My suggestion, but other have different suggestions and it really depends on what you want, is to have about 30GB as / and rest as /home or data.

---

### Post by Old Jimma on 2020-12-29
Thanks to  Hagar Delest, 1fallen, and oldfred:

I appreciate your replies. I guess that it does not make any difference. Things are working fine, so I'll just leave it as is.

Many thanks!

I'll close this thread as being solved now!

THANKS!
Old Jimma

---

### Post by Hagar Delest on 2020-12-29
oldfred is correct, that's needed actually. UEFI is replacing the BIOS IIRC.
I thought your partition was too big at first but it's a mere 0.5BiB in fact (mine is 273MiB for a 128GiB SSD).
Note that there was an issue with the Ubuntu 20.10 installation, it could not install on non-UEFI disks. I experienced that on my old laptop.

For the record, I've 2 partitions (20GiB each) for the system (root), plus other partitions for /opt and user documents. I install on 1 partition of course but when upgrading the distro, I do a brand new install of the new distro on the other partition. This way, I'm sure I can go back to the previous version in case something goes wrong with the new one. More work to retrieve the customization, but this way I'm sure the system is free of any old or deprecated things that could influence the performances.

---

