---
title: "Ubuntu grub boot-repair turned my storage hard drive into efi"
date: 2014-02-04
forum: General Help
---

### Post by nichollsjeffrey on 2014-02-04
So I'm a noob Ubuntu user & had the following happen.

 I have Debian, Ubuntu, Ubuntu Studio & SteamOS all installed side by side on a spare 500gb hard drive that I had. I wanted to get rid of Debian & SteamOS so I deleted their partitions but the problem is that one of those partitions had the grub boot loader on it, so the next time I booted my pc I come to the grub error command line screen, which I had no idea how to use even after I looked up info. So I made a Ubuntu iso on a USB to run the try ubuntu just to use the terminal. I used boot-repair to put the grub back on the 500gbs & it was all working well when.......... I booted back to my SSD (I have Windows on a seperate hard drive, I just select the 500gb drive to boot from when I want Ubuntu's) low & behold my main 4tb storage drive is missing, I go to disk management & find that it's now an efi not ntfs, please someone tell me that I haven't just lost the 2tb's of irreplaceable data off of it & that I can change it back to ntfs with my data still on it?

Everytime I eff around in Ubuntu I think, gee I should really unplug every other hard drive that Ubuntu aren't installed on so that I don't eff anything up. I will throw my computer into a lake if that hard drive is erased.

---

### Post by fantab on 2014-02-04
If you've run Boot-Repair did you make note of the Link to BootInfo Summary? If you did then post the link here. Or else 'create Bootinfo Summary', note the link  and post it here...

---

### Post by oldfred on 2014-02-04
Post link from BootInfo report.
But Boot-Repair never creates partitions, you have to have those partitions existing for Boot-Repair to install or reinstall in different boot mode.

It may have seen a NTFS partition with boot flag and tried to make it the efi partition if you booted in UEFI mode and had it reinstall grub in efi partition, but then that may be a grub install issue. 
Best to boot Boot-Repair in the same mode as installs or confirm that you want different repair mode.

---

### Post by nichollsjeffrey on 2014-02-04
Nope didn't get that link :(. So if I go into disk utility I'm able to mount that drive & see the files. It said it was an efi partition but after I updated ubuntu it's changed to a Basic Data Partition. I tried to look at the drives it didn't mess with to see what they were partitioned as to see if I could change it to them. I might go boot to windows & see if that ubuntu update has fixed my drive for me.

---

### Post by nichollsjeffrey on 2014-02-04
So here are screenshots of my hard drives in Disk Utility, hopefully the links work. So in ubuntu they all don't auto mount but in windows my 2tb & 1tb show up & work fine.

[http://imgur.com/a/NR8ps#0](http://imgur.com/a/NR8ps#0)

---

### Post by nichollsjeffrey on 2014-02-05
I managed to change the partition to a Microsoft Basic Data Partition & even though in ubuntu it shows up as a Linux Data Partition it now works in Windows again. I should get a job at Canonical ;)

---

### Post by oldfred on 2014-02-05
It is a 4TB drive which has to have gpt partitioning.

And with gpt(GUID) partitioning a boot flag changes its GUID to the ESP or efi partition, not a data partitions GUID.
But a boot flag should only be on the smallish FAT32 efi partition used for efi boot file, never on any other partition.

---

