---
title: "dual boot ubuntu 10.10, reinstall win 7 problem"
date: 2014-03-02
forum: General Help
---

### Post by carvish on 2014-03-02
Has anybody ever seen this before? Long story short, I had to do a reinstall of my win 7 on my dual boot system. I disconnected the drive with ubuntu Reinstall went "normal" , after install and reconnecting Ubuntu drive,  My grub bootloader popped up, I hit Ubuntu 10.10 and it promps me for a user name and password. Is there a way to disregard this password? Grub starts normally, Ubuntu promps me, and win7 asks for the install disk. Hmmm? The message I am prompted by Ubuntu is

 " gamera-system-product-name login:"

 I tried a recovery, after  "repair broken packages" and  "update grub bootloader" I receive this

 " root@gamera-system-product-name:~#"

any ideas?

---

### Post by Impavidus on 2014-03-02
Sounds like the normal console login. You get that when for some reason the GUI doesn't start. Maybe you can login and start the GUI with **startx** (?).

I may have to remind you that Ubuntu 10.10 has been unsupported for almost two years. I suggest you backup some files and install a supported release.

---

### Post by carvish on 2014-03-02
Thank you I'll try this, the reason I have never updated Ubuntu is I tried with 11.04, I had nothing but problems so I stuck with something that worked. Tho I would love to run the latest, Im not sure if I would have to go through all the little critters to get to the salamander, the Narwhal left a bitter taste , lol

---

