---
title: "Be sure to install microcode or you will have problems with suspend."
date: 2018-04-28
forum: General Help
---

### Post by Cavsfan on 2018-04-28
I installed Bionic Beaver 18.04 LTS yesterday and today when I suspended it by pressing a key on my USB keyboard it would get to the lightdm screen but after entering password, the screen displayed "no signal".
After a few times of seeing this, I just happened to press Cntl+Alt+F2 to login to tty2 and then pressed Cntl+Alt+F1 to get back to tty1 and an error displayed about the microcode being missing and to install it.

Then I went into Synaptic and installed intel-microcode and that fixed that problem. If you have an AMD processor install the amd-microcode package. 

Also if you have a USB keyboard and mouse like most new computers use, I suggest you follow this [[COLOR=blue]post[/COLOR]]("https://ubuntuforums.org/showthread.php?t=2388336&p=13758866#post13758866") to give your keyboard and mouse the ability to wake the system from suspend.

After you do all of this reboot your computer to test it out.

---

