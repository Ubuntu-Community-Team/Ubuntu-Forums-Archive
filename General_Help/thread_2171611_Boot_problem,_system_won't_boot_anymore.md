---
title: "Boot problem, system won't boot anymore"
date: 2013-08-31
forum: General Help
---

### Post by mrzx4p5-c4u6to-hwbqsl9 on 2013-08-31
Hi,

back from 2 weeks vacation, my system started (Ubuntu 13.04, 64bit), but showed errors like "partition mounted read-only" and strange behaviour of running programs resulting in automatic closes of them, then a freeze of the system after the screen went black.

Afterwards I couldn't start my system, grub2 won't show up, just a blinking line.

A start with a CD system (Try Ubuntu) showed me, that I could access the partitions, the data was still there. I then realized, that I could tell my BIOS to show a boot menu. If I choose the second drive where Ubuntu is installed, the system comes up and runs (at the moment) fine.

So I guess something shot my boot loader, which should be grub2. I furthermore guess, that the first drive, /dev/sda, has no information how to start the second drive /dev/sdb with Ubuntu 13.04, so I assume I have to reinstall grub2. 

That's the point you come in, I don't know how to do this and if it's indeed the solution to my problem. Boot images and stuff are in /boot on /dev/sdb2, the system running right now. Should I issue "grub-install /dev/sda"? Or would you recommend other things first for further analysis?

Any help is greatly appreciated!

Cheers!

---

### Post by bkline on 2013-08-31
Here are some pages which might be helpful:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

Good luck!

---

### Post by Impavidus on 2013-08-31
[Boot-Repair?](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mrzx4p5-c4u6to-hwbqsl9 on 2013-09-02
Hi,

thanks for the very useful links!

As a matter of fact, it showed that the problem was in the BIOS, the second hard drive wasn't in the boot-from-section anymore, but the first. Switching to the second again solved the problem, grub was still installed. Maybe the BIOS' battery was empty after two weeks vacation - I guess it shouldn't, as the motherboard is not older than 2 years :(

Anyway, system is running fine again, thanks again for your quick help!

Cheers

---

