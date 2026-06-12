---
title: "I install ubuntu and i can't start it"
date: 2017-04-06
forum: General Help
---

### Post by ulkra on 2017-04-06
Hello, i have a HP computer (HP Pavilion Slimline s5702la, 1TB, 4GB RAM, is good)
and i had 2 windows 7 installed, because i use one to program and everything that is... job, etc. And other when i have my stuff. I decided to install Ubuntu to, the install is finished but when i restarted my computer i just see the windows Shell where i can see my 2 Windows 7 options to start windows, but nothing about Ubuntu. (i mean... this [http://i.imgur.com/ik2A7fy.jpg](http://i.imgur.com/ik2A7fy.jpg) )How can I start Ubuntu?

EDIT: is not the first time i install ubuntu and i've used ubuntu for like 1 year

---

### Post by yancek on 2017-04-06
That's the windows boot menu so that means you didn't install the Ubuntu Grub bootloader.  You can create an entry with bcdedit on windows to boot Ubuntu but it is much easier to install Grub.  Are both your windows 7 systems using MBR or is this an EFI install?  You aren't trying to do a WUBI install are you?  Which installation type option did you select with Ubuntu, the manual "Something Else" option or the install Alongside?  Might be best to get more details which you can do by going to the site below and getting the boot repair software.  You can do it either by booting the Ubuntu install DVD or downloading it on windows and burning it as an image to a CD and reboot the computer with the CD set to boot first.  There is an option to Create BootInfo Summary, select that and post a link to the output here and don't try any repairs.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

