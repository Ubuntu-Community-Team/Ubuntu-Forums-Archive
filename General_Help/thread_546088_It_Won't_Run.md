---
title: "It Won't Run"
date: 2007-09-08
forum: General Help
---

### Post by drndrw on 2007-09-08
Hey guys. I am really new to Ubuntu, and I am currently trying to install it. Well actually, I'm going to run Xubuntu. But anyways, I took the hard drive out of my computer the other day, put a new, clean one in, and I tried to install Xubuntu by popping it into the CD drive. Though when I did, nothing happened. I'm not sure what my problem was, whether it was that I had a blank hard drive in or that I simply didn't do the right thing for installing. Could someone tell me what to do so I can be running Linux by tonight maybe :P? Thanks.

---

### Post by apetresc on 2007-09-08
The problem is most likely that your computer's BIOS is not set to boot from a CD drive. To change this, you have to enter the computer's BIOS setup screen. Right when you first boot your computer, it will probably tell you at the bottom, something like "Press F12 for Setup" or something like that. Usually they are either F1, F2, F8 or F12. Try them all.

Once you are in the BIOS setup screen, I can't give you exact instructions because every manufacturer has a slightly different BIOS, but the main idea is that you want to look for a section named something like "Boot Device Priority". Make sure that the CD-ROM drive is set HIGHER than the hard drive. Then put the Ubuntu CD in the drive again, and try rebooting now, and you should be at the LiveCD prompter! :)

---

### Post by drndrw on 2007-09-08
Oh, okay. And then it should pick up the hard drive? Thanks.

---

### Post by sumguy231 on 2007-09-08
Yes, once it loads the installer from CD it will detect your hard drive so it can install to it. I should add that you also need to make sure that if you burned the CD yourself, you burned it correctly, as if you just made a data cd with the .iso file on it, that will not work. You need to use your CD burning app's 'burn iso image to cd' or what have you option.

---

