---
title: "Help with Windows Boot Loader"
date: 2008-01-24
forum: General Help
---

### Post by Mechanix350 on 2008-01-24
First off I would like to apologize to any veteran users if you find this post repetitive or annoying in any way. 

Here is my situation: I have Windows XP and Ubuntu 7.10 installed on a single hard drive. I would like to reconfigure my Windows boot loader to boot to both XP and Ubuntu. My problem is is that I do know know the code statement to put into the BOOT.ini file. I imagine it would go something along the lines like this:
 
multi(0)disk(0)rdisk(0)partition(3).......

Since the Ubuntu operating system is listed as the 3rd partition (the swap file being #2). I don't know what file to tell the boot loader to point to. If this is even possible what is the name and location of the file that boots Ubuntu and how would I plug it into this code statement. I appreciate any help you give. Thanks for your time.

---

### Post by sekinto on 2008-01-24
You could try this:
[http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last](http://www.linuxdevcenter.com/pub/a/linux/2006/05/08/dual-boot-laptop.html?page=last)
...but it sounds complicated.

You might just want to boot GRUB and have WinXP as a choice.

---

### Post by logos34 on 2008-01-24
Why do you want to use windows bootloader rather than grub?

You know, you can easily restore the windows bootloader over Grub at any time using either the XP install cd or super grub disk.

---

### Post by p_quarles on 2008-01-24
> **sekinto said:**
> You might just want to boot GRUB and have WinXP as a choice.
I agree. That is by far the simplest and most user-friendly option.

Here's a guide to using an Ubuntu installation disk to install GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Mechanix350 on 2008-01-28
Thank you for all the help.

---

