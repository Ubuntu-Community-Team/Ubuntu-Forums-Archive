---
title: "[SOLVED] Dual boot issues w/ win xp pro"
date: 2008-06-21
forum: General Help
---

### Post by goehringoehring on 2008-06-21
I have recently installed Ubuntu on my Dell Dimension 2350, with two separate hard drives. [Windows being 0 and Ubuntu being 1] My windows installation worked great before I installed Ubuntu. After I did the installation Ubuntu works great and I love it, but when I try to boot into Windows, it will get about half way started then I get the BSOD. Any ideas? May this be an issue with GRUB? Am I able to convert back to the Windows Boot Manager and still include Ubuntu? Can anyone tell that I am new to the Linux platform? LOL
Any help will be appreciated greatly!!

---

### Post by VMC on 2008-06-21
The BSOD is troubling, it appears the Grub handed off to Windows the correct information. Maybe something with Windows somehow. Anyway, first things first.

Output a couple of things. From Terminal (Applications-Accessories-Terminal)
Type the following:

```
sudo fdisk -l
cat /boot/grub/menu.lst
```

From there we can determine what to do.

---

### Post by goehringoehring on 2008-06-21
Here is what i get when i type those commands.
[IMG]http://img.photobucket.com/albums/v80/Fashion_Fouxpaux/ubuntuscr/terminal1.jpg[/IMG]

---

### Post by goehringoehring on 2008-06-21
This is what i get on the second command.
[IMG]http://img.photobucket.com/albums/v80/Fashion_Fouxpaux/ubuntuscr/terminal2.jpg[/IMG]

If it is something with windows, I can re install it as a last resort, I have a full backup from a week ago, not much has changed. but if possible id like to try and fix it first.

---

### Post by goehringoehring on 2008-06-22
No need to worry any longer, I have figured out what the problem is. My main problem had nothing to do with GRUB or Ubuntu. I really didn't think that there was anything wrong with the Windows installation, but I think that when I ran the Ubuntu install it somehow corrupted a few files on the Windows side. I only say this because before installing Ubuntu, it worked fine and after installing, I would get the BSOD when booting Windows. 

Solution - 
     Just for kicks and giggles last night I popped in the Windows install disk and started the recovery console. Did a couple of different scans and nothing came back irregular. Until I did a chkdsk /p. It showed that there were in fact a few corrupt files on the windows drive. After I discovered that I ran a chkdsk /r, rebooted and viola! No more BSOD YAY!!!

**EDIT**
Thank You VMC, the two little lines of code you put my way helped me get the problem solved. I am starting to learn more and more every day about the Linux platform.

---

