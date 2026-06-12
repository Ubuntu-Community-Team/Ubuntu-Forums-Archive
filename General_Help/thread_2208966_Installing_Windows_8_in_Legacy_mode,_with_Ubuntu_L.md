---
title: "Installing Windows 8 in Legacy mode, with Ubuntu Linux already installed."
date: 2014-03-03
forum: General Help
---

### Post by PotatoHead007 on 2014-03-03
Hi, so i have a question.
I am a gamer, and i love playing League. I installed it with POL, but no matter what i try, i always get bad fps. Also, some other games ar enot supported by POL.
So i want to re-install Windows 8 on my Laptop. The Laptop originally came with UEFI and Windows 8, but i deleted Win8 and changed to Legacy.
My question is this, can i install Wind8 in legacy mode, and if yes, how do i go about doing it without breaking my Ubuntu 12.04 32bit installation?
Any help would be great.

PC specs:
Intel i5 3210M
4GB RAM
nVidia GeForce 650M/Intel HD 4000
HDD: 750GB

PS: If its difficult to install Windows 8 like this, then just answer my first question(Win8 legacy support), because i am going to do a fresh install of Ubuntu 14.04 in April. Thanks again :)

---

### Post by oldfred on 2014-03-03
If you installed Ubuntu 32 bit you must have also converted drive from gpt to MBR(msdos). 

Then you should be able to install Windows, but Windows requires a primary NTFS formatted partition with the boot flag. If you have used all 4 primary partitions you will have to reorganize. Your vendor image cannot be used as its product key is in the UEFI memory and is only for UEFI. You have to purchase a new copy of Windows 8.

Also with a new computer like you have with 4GB of RAM you would be better off with 64 bit Ubuntu.

Currently only 64 bit versions support UEFI.
Windows only boots from gpt partitioned drives with UEFI.
Ubuntu can boot from gpt partitioned drives with UEFI or BIOS.
Both Windows & Ubuntu only boot from the 35 year old MBR(msdos) partitioning with BIOS.

How you boot installer is how it installs. 

More info on Windows.
 [http://www.eightforums.com/](http://www.eightforums.com/)

---

### Post by PotatoHead007 on 2014-03-04
Ok, thanks for answering! I have decided to wait for Ubuntu 14.04, and then Install my Windows 8 in UEFI, then dual-boot with Ubuntu 64bit.
Thanks again ^^

---

