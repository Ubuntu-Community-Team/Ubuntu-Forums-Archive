---
title: "Help, stuck after installation!"
date: 2020-06-03
forum: General Help
---

### Post by bikerviking on 2020-06-03
Hi.

I used a flash drive and Lili to make a live USB to format my notebook. I used the latest iso from Ubuntu's official website, 20.04.

I have a SSD [128GB] and a HDD [1TB], so I used the LVM option and made some partitions;

SSD

550MB to efi 

100MB to boot

"/" To rest


HDD

16GB to swap

20GB to var

/Home keep the rest


When installation asked me where to install the boot loader I selected the whole SSD.

After it finished copying files it asked me to restart and then to remove the "medium" and press enter.

After that it restarted but got it stuck at Dell's logo and seems not to go anywhere. 

After 20 minutes or so shutdown and turn it on again, grub loads up with 3 options; Ubuntu, advanced options for Ubuntu and uefi firmware update.

Ubuntu stuck as the same before.

Uefi restarts and boots the bios

I tried recovery mode in advanced options and it writes a lot of stuff, but the last line reads:
"---[ end of kernel panic - not syncing: VFS: unable to mount root FS on unknown-block (0,0) ] ---"

Did I made something wrong? How to fix it? Help!

---

### Post by Autodave on 2020-06-03
Are you trying to dual boot?

---

### Post by bikerviking on 2020-06-03
No, I formatted all my discs, at least I meant to.

---

### Post by oldfred on 2020-06-03
Have you updated UEFI from Dell?
And updated firmware for SSD?

What model Dell?

Dell - All
[https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup](https://www.dell.com/support/article/en-is/sln298524/how-to-use-and-troubleshoot-the-inspiron-17-5759?lang=en&ref=topsolutions#Resetting_System_Setup)
How to Install Ubuntu Linux on your Dell PC 
[https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en](https://www.dell.com/support/article/us/en/04/sln151664/how-to-install-ubuntu-linux-on-your-dell-pc?lang=en)

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by bikerviking on 2020-06-03
ULTRA SLIM I15-7572-A30C INTEL CORE I7 16GB (GEFORCE MX150 COM 4GB) 1TB 128GB SSD FULL HD 15.6" W10 - DELL

I don't have the exact serial number. 
I had a previous installation of Ubuntu 18.04 if I'm not mistaken, but I wanted a fresh start and I decided to update it to 20.04.

I don't believe that I updated it's firmware.

---

### Post by TheFu on 2020-06-03
> SSD
550MB to efi
100MB to boot
"/" To rest

That looks like the efi and boot sizes are backwards.  Boot should be 500MB-750MB and efi of 100MB is overkill.   Kernels go into /boot/   EFi stuff goes into /boot/efi/  which is where the efi FAT32 partition gets mounted.  The others should be ext4 unless you have a reason for some other file system.

Size matters.  ;)

---

### Post by TheFu on 2020-06-03
/Home shouldn't be capitalized.  Should be /home.   Unix is always case-sensitive.

usernames and hostnames should be lowercase to avoid issues too.  Most of the time, it shouldn't matter - until it does.  Then your life will suck.

---

### Post by oldfred on 2020-06-03
With nVidia you need nomodeset to boot installer.
And new versions now offer to install the correct nVidia driver, but if restricted extras not selected you again need nomodeset to boot into your install.

At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

