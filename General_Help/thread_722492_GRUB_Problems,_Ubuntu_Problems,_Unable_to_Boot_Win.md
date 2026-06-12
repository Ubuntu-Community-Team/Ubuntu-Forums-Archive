---
title: "GRUB Problems, Ubuntu Problems, Unable to Boot Windows XP from GRUB, HELP PLEASE!"
date: 2008-03-12
forum: General Help
---

### Post by OllyNewport on 2008-03-12
Ok, right, Brand new to Ubuntu, and have used some dual boots in the past, but haven't for a loooonngg time.

Specs:

Windows XP - Ubuntu 7.10
100GB HDD - 10 Partitioned for System Restore
ATi Radeon Xpress 200M Video Card
1GB RAM
1.68 Ghz AMD Turion64 Processor

Anyway this is my time line:

I have a Compaq Presario V5000, 100GB of memory -  1 Partition for System Restore 10GB

OS's installed:

Pre-Installed on Laptop when shipped -  Windows XP SP2
Ubuntu Linux 7.10

Right when I first installed Linux I encountered problems with the install, so I had to re-install it, and so I have 2 7.10 Ubuntu OS's on my system.

When I partitioned the drive, I think something went wrong, and Ubuntu ended up installing it's self onto the whole drive, that Windows XP is also on, so both have ended up sharing each others drive (I think).

So basically my problem is that GRUB hasn't added XP to the OS list, and manually adding it, several different ways hasn't work, but then I'm not sure onto what code I have to use, as each time I run GRUB either gives me a 13, unable error.

So does anyone have an idea as to what is going on?

ALSO! Before you say just run the XP system restore disk and try pressing (R) fixmbr that won't work as each time I try to do that, my laptop decides that it want to turn it's self off for no reason at all.

ANY HELP PLEASE?

Thanks :confused::confused::confused:

---

### Post by sandysandy on 2008-03-12
please post output of 

[COLOR="Blue"]sudo fdisk -lu[/COLOR]

regards

---

### Post by OllyNewport on 2008-03-13
Never mind, I found that windows xp was currupt when Ububtu was installed without a partition, and so I had to reformat everything, I will post my resalts now that I have no data to risk, with a dual boot Ubuntu/XP combo.

---

### Post by sandysandy on 2008-03-13
> **OllyNewport said:**
> Never mind, I found that windows xp was currupt when Ububtu was installed without a partition, and so I had to reformat everything, I will post my resalts now that I have no data to risk, with a dual boot Ubuntu/XP combo.

all the best :)


here are some links to dual booting:-

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)


regards

---

### Post by reeseslover531 on 2008-03-13
If you are starting fresh it shouldnt be too hard just remember to install xp first

---

