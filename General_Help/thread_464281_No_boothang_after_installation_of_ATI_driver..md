---
title: "No boot/hang after installation of ATI driver."
date: 2007-06-04
forum: General Help
---

### Post by ozstriker on 2007-06-04
Hi guys, I've just installed 7.04 and am having a bit of a problem with the install. (well actually a couple, but the windows problem belongs somewhere else)
I installed everything fine, and rebooted into my install. First thing I did was add some repositories, and I did an apt-get update after that, but that's it. 
Then, I used the "restricted graphics drivers' option in the system menu to install ATI drivers for my x800xt. I needed a reboot for this, but after the reboot, I can't boot into Ubuntu.
It freezes during the loading bar screen, and completely stops responding. The keyboard lights flash on and off also. 
Now I figured that this might be a problem with the driver, so I tried booting into recovery mode, but the same thing happens (except that I can see there's a kernel panic because there's no loading bar isntead)
So I can't get into my system to fix it.
I tried editing xorg.conf using the live CD, but changing the video driver to "vesa" didn't do anything (I may have got it wrong though, my knowledge of that is a little rusty.)
So any ideas people? How do I go about fixing this?

---

### Post by ozstriker on 2007-06-04
Bump.
Anybody?

---

### Post by ozstriker on 2007-06-05
bump again.
Does nobody have any idea? I'd really like to get this fixed, I have no working bootable OS on my computer anymore :(

---

### Post by eggdeng on 2007-06-05
Look in the /etc/X11 directory ```
ls /etc/X11
``` to see if you can find a file that looks like a backup of xorg.conf made when you updated the drivers. It might be called xorg.conf.original-0. If so, back up the current xorg.conf```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bkp
``` and then rename the file you found ```
sudo mv /etc/X11/xorg.conf.original-0 /etc/X11/xorg.conf
``` Reboot & pray.

---

