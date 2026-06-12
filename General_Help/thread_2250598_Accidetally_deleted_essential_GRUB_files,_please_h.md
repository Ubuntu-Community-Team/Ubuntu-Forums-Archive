---
title: "Accidetally deleted essential GRUB files, please help!"
date: 2014-10-29
forum: General Help
---

### Post by dillorr on 2014-10-29
Hello! So a little bit of backstory... 
Yesterday I was doing some hard drive cleaning on my ASUS U52F (intel i3 processor), and re-formatted a partition containing an older version of Ubuntu. Much to my dismay, the files governing GRUB were apparently contained in that partition. So i boot into GRUB rescue mode and proceed to try to boot manually from my root directory in order to repair. Unfortunately, when i found the location of linux.mod, loopback.mod, etc., insmod linux refuses to find the correct file it calls for. After looking around some more, my problem seemed to be only fixable with the use of an Ubuntu install disk, which I burned sucessfully from a friends computer. After trying to boot from the disk, I am met with a black screen with a white blinking underscore for an indefinite period of time. I have entered my computers BIOS and set disk boot to priority 1 to no avail. I am thinking that my computer is unable to fetch information from the disk but my disk drive has never had problems. 

I have tried everything I can think of and no dice. All of my files should be completely intact, I just need to actually get into my system. Any suggestions are welcome, please help . Thank you.

---

### Post by kc1di on 2014-10-29
[This page ]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")should get you going again.

---

### Post by ajgreeny on 2014-10-29
Boot-Repair in my signature (run from a live DVD or USB) may help you get grub back where it should be, even if you have removed the partition where the files used to be.

---

### Post by dillorr on 2014-10-29
> **kc1di said:**
> [This page ]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")should get you going again.
Thanks for the information. This would be very helpful if I could actually boot from the CD but for now I will try to use boot-repair to whip GRUB back into shape as ajgreeny suggested.

---

### Post by kc1di on 2014-10-30
Boot-Repair is a good tools hope it works for you :)
Usually when you can't boot from the live cd it's beacuse of a video card problem. you may want to try the nomodeset argument in the boot line.
good luck .

---

