---
title: "Hard drive permissions, GRUB, adding multiple Hard Drives from old to new computer"
date: 2017-12-17
forum: General Help
---

### Post by styrofoam-feet on 2017-12-17
A friend's parents gave me their old Desktop as they got a new one. I don't know why, i7 11gb RAM. All they do is Facebook and Amazon. Anywho, it is faster than my Frankenstein, so I want to operate. I did a fresh install of 17.04. on the i7. My Frankenstein has 3 SATA HDDs. My master hard drive is a dual boot with 14.04 (was a good year) and Ubuntu Studio 16.04. So here are my questions:--

- Can I add 3 new hard drives at once to my new computer?
- If said 3 hard drives are added (1 of which has a dual boot of two separate operating systems) will I kill GRUB?
- If I don't kill Grub, it should boot into 17.04, and from there I should be able to modify GRUB?
-Now here is the part I'm worried about: Permissions. With a Dual-boot being added that has two different permissions settings from previous OS's, what kind of nightmare am I in for?

My possible alternative:
Take all my stuff off Frankenstein hard drives, and wipe them so I can add them to the new comp, then install all the operating systems I want after things are running smoothly with the hardware additions.

What I want to happen
- I add 3 hard drives and GRUB recognizes my other OS's upon the 1st startup and life moves forward.

Thanks!):P

---

### Post by oldfred on 2017-12-17
You could add all the drives.
And if you use same userid and password, it may just work.

But new system will be UEFI, was old system UEFI or BIOS?
And then new drive is gpt and older drives may be gpt or MBR(msdos). You can continue to use MBR, but eventually should plan on converting drives to gpt.

New UEFI systems have CSM, so you should even be able to boot install on old drive if BIOS install.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I typically have multiple drives, and sometimes just reset my ownership & permissions on my data only. Never on / (or any system partition).

Do you have separate data partitions and what format, Linux like ext4 or some NTFS?
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

Make sure when you plug drives in, original drive is in first SATA port, SATA0, and then use ports in order. Do not skip any. IF also a DVD make it last in order. And some systems have ASmedia ports to add more ports than Intel default and those do not work with Linux, even for DVD.

---

### Post by styrofoam-feet on 2017-12-17
That's an interesting distinction that I had not considered. Name the new distro, same as the old one, with the same password, and I may be able to keep from messing with the settings. I guess the big thing is, is that I don't really know how the permissions work on my hard drives. I seem to have enabled access to my slave hard drives about 2 folders deep before being prompted for the password. I don't know why it does that...This is Ubuntu 14.04 btw. Both pcs have bios. On my older SATA drive, it is partitioned with Ubuntu 14.04 and Ubuntu Studio 16.04. The newer drive was Windows 7, but I reformatted it for ext4, and installed Ubuntu 17.04. If I could retain my distros, that would be convenient, I'm hesitant because I don't want to lock myself out of one of my drives. If that is even possible.

---

### Post by oldfred on 2017-12-17
Does each drive's install have its boot loader installed to the MBR of that drive. That would be best case and then you can separately boot each from UEFI/BIOS.

Do not run any auto-fix offered. Only use Advanced mode of Boot-Repair if more than one drive or more than one install.

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

