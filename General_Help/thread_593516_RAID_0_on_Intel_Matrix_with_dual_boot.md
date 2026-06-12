---
title: "RAID 0 on Intel Matrix with dual boot"
date: 2007-10-27
forum: General Help
---

### Post by Nzer24 on 2007-10-27
Currently, I have a dual-boot system of Ubuntu and Windows XP on a 500GB hard drive. I have a pretty  nice computer over it, but it's frustrating to have such significant read/write times for both my games on XP and my internet browsing / programming / other stuff on Ubuntu. So, I'm going to try a two or three disk RAID 0 array setup for both my files and my operating systems. I have "Intel Matrix" RAID ability on my motherboard, which I understand to be a low level software RAID. I need a driver for this, which I have, but it's only for XP. I think I can just partition equal parts of the drives for use in the Linux part, but I'm not sure how I can install Ubuntu over three partitions on RAID 0. I also heard that I can't install GRUB on the collective MBR  of the drives, so I will have to do so on the MBR of my old drive. The only thing I don't understand is how to install level 2 of the bootloader on a seperate drive that is also a RAID array. I could just keep it on the old drive, but then how should I configure menu.lst to boot the RAIDed systems? 

Any answers would be helpful.

Just so you know, my specs relevant to this are:
500GB Seagate Barracuda sata-300 hard drive
considering multiple 160GB WD Caviar SE16 sata-300 hard drives
Intel DP35DPM motherboard with P35 northbridge and ICH9 southbridge using Intel Core 2 Quad Q6600 processor
Ubuntu Gutsy
Windows XP Home SP2

---

### Post by clparker on 2007-11-10
Yeah man, I have Intel Matrix Raid too, and I've never been able to figure out how to do a dual boot on it. I'd love to know if anybody ever figures this one out.:confused:

---

### Post by fjgaude on 2007-11-10
Well, lots of folks have been at this for months without any solution, that I know of.

The new drives that are coming out from Hitachi that have seq reads of 134 MB/sec makes using just one drive for bootup nice, with a raid5 array for data, one with four or more drives. I'm sure Seagate will follow suit soon, very soon.

I've been thinking of the type of motherboards you two have. Tell me if you can, does the SATA controller, the RAID one, run off the PCI-Epress bus, and if so is it x1, x4, or x8?

Just an after thought, booting from raid is just so risky... it's so easy for things to not work and then you have one big problem to get things sorted out again.

---

