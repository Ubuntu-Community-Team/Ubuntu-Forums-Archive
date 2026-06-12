---
title: "Are MBR - boot menu  /boot - GRUB all the same?"
date: 2008-06-26
forum: General Help
---

### Post by sofasurfer on 2008-06-26
Heres what I think I know...

1. The boot menu is created by the menu.1st. 
2. GRUB is contained in the /boot directory.
3. GRUB can be installed on the MBR ( master boot record ) or on the "/" partition or any partition in the computer.

Heres what I do not know...

4. When the boot process fails, is the part that need replacing the GRUB file or the entire /boot directory?
5. When GRUB can be mounted on the MBR or any other partition, is that to say that the entire boot directory is relocated to the desired partition and then the /etc/fstab file must be edited to mount this directory?
    I would understand that process quite simply, but the tutorials make it sound quite a bit more complicated.
6. How does a person who know no better learn where the boot loader has been installed?

Since I don't understand all the lingo yet I am not sure how to phrase the questions. 

When I installed Ubuntu I had the option of differant boot locations. But my choices were unsuccessful. I think I chose the MBR but do not remember. My file system does contain /boot. 

Hmmm, confusing. Please answer what you can and every little bit of info will start filling in the gaps in my understanding.

---

### Post by chewearn on 2008-06-27
When in doubt, read wikipedia:
[http://en.wikipedia.org/wiki/GNU_GRUB](http://en.wikipedia.org/wiki/GNU_GRUB)

[B]1. The boot menu is created by the menu.1st. 
[/B] Yes, except it's menu.**l**st, not menu.**1**st

[B]2. GRUB is contained in the /boot directory.
[/B]Specifically, /boot/grub, excluding stage 1, which could be located in the MBR.

[B] 3. GRUB can be installed on the MBR ( master boot record ) or on the "/" partition or any partition in the computer.
[/B] Yes.

[B]4. When the boot process fails, is the part that need replacing the GRUB file or the entire /boot directory?
[/B]The question is too broad.  Many things can contribute to boot failure.

**5. When GRUB can be mounted on the MBR or any other partition, is that to say that the entire boot directory is relocated to the desired partition and then the /etc/fstab file must be edited to mount this directory?**
    
Grub and /etc/fstab are two different things.  Grub is the bootloader, while /etc/fstab is a configuration file.


**6. How does a person who know no better learn where the boot loader has been installed?**

Not sure on this one.

---

### Post by plucky on 2008-06-27
See this link for everything you want to know about Grub and more
[The Grub page](http://users.bigpond.net.au/hermanzone/p15.htm#orientation)


Good Luck

---

