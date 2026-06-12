---
title: "Trying to resize partitions using GParted but my computer won't let me boot from USB"
date: 2016-03-25
forum: General Help
---

### Post by jedi_knight2 on 2016-03-25
Hello everyone!

I am trying for some hours now to boot my USB, but it won't even show as an option at the boot order(I tried putting the HDD in the bottom but that didn't help either).
When I first installed ubuntu I did it using the same USB i used then but for some reason it won't work now! I want to create a partition but my hard drive needs to be re-sized first. There is no way to do that(that I know) without using _GParted_ when booting from the ubuntu iso installation file.

I have visited lots of sites and I can't find something that can help me.(I found a way with a program called PLoP but I don't have a CD with enough space to use it)

---

### Post by grahammechanical on 2016-03-25
You might need to go to the section where you set which hard drive to boot from. After I first set up the BIOS to boot from a USB port I then had to think of the USB stick as an external USB drive because that is how the BIOS was seeing it. Changing the boot order did not work but going into the hard drive settings option and moving the external USB drive to the top does work.

Regards

---

### Post by jedi_knight2 on 2016-03-25
My BIOS menu does not have an option like that, I will now try to make a bootable USB from the computer I used the first time installing ubuntu.

---

### Post by jedi_knight2 on 2016-03-25
Update: I tried using the USB on the other computer and it worked smoothly with no problems, I tried using VirtualBox too with the ISO file and that worked too. It seems that something is wrong with my computer's BIOS...

---

### Post by Bucky Ball on 2016-03-25
*Thread moved to **General Help**.*

I have a similar problem on my laptop where the BIOS settings seem to do nothing about booting from USB but hitting F12 to get to the boot device menu and selecting USB works fine.

You could try that. F12 is common to get to the boot device menu, but your machine might use another key. You hit that key instead of whatever you would to get to BIOS at boot.

---

### Post by jedi_knight2 on 2016-03-25
My machine does use F12 but that still didn't work... Anyway I found a way around and now it works fine so I'm marking this as solved, thanks for the suggestions anyways!

---

### Post by Bucky Ball on 2016-03-25
> **jedi_knight2 said:**
> Anyway I found a way around and now it works fine so I'm marking this as solved, thanks for the suggestions anyways!

!!! We don't do that here! 

Please share with the community how you fixed your issue. 'I fixed it, bye' gives back nothing and does not help future travelers. :D

---

### Post by jedi_knight2 on 2016-03-27
I fixed it by putting this [https://sourceforge.net/p/boot-repair-cd/home/Home/](https://sourceforge.net/p/boot-repair-cd/home/Home/) in a disk. 

WARNING: If you put it in a live USB it may not boot in it, so I suggest burning it in a CD/DVD for best results.

---

