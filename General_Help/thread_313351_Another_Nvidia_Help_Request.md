---
title: "Another Nvidia Help Request"
date: 2006-12-05
forum: General Help
---

### Post by DoctorDemento on 2006-12-05
I currently have the i386 release of edgy installed and was working fine with my on-board video. I upgraded the graphics with an XFX GeForce 6800XTreme AGP 8X and now x is crashing on boot. (Note: I do have dual boot with M$ and the card works fine.)

I wanted to upgrade Ubuntu to the x86-64 version but found that once the live cd entered the desktop the screen goes to random colored pixel gobbledy gook (spelling?). I tried this with other distros with the same result.

I found the "bleeding edge drivers" on Alberto Milone's home page but here is my question. Do I re-enable my on-board video and switch ports, install x86-64, and follow the directions on his page or do I have other problems. 

Also, please note that I am still very new to Linux as far as things such as this (I have done a little command line work). Before now everything has just worked.

---

### Post by CatKiller on 2006-12-06
I understand that you may have more difficulty with the 64-bit version than the 32-bit.

Does ```
sudo dpkg-reconfigure xserver-xorg
``` and selecting the **nv** driver help? If not, then how about [this]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")?

---

### Post by tommcd on 2006-12-06
Perhaps this guide may help:
[http://doc.gwos.org/index.php/Nvidia_Intel_Integrated](http://doc.gwos.org/index.php/Nvidia_Intel_Integrated)
Just back up your xorg.conf file before doing this just to be safe:
(sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak)
Hope this helps.

---

### Post by DoctorDemento on 2006-12-06
Thank you for the replies. I just got home from work and have to go xmas shopping with the wife. I'll try them if time permits afterwards.

UPDATE: I have found one of my major problems. The XFX card came with a thick booklet and I had hoped that it was full of good information, but alas it was not. Just about 4 pages of installing the drivers in windows... IN 20+ LANGUAGES! This allowed me to make the following mistake. The card comes with dual DVI outputs (I was using the top) and I never thought that there would be any problem attaching to either one, after all, windows didn't care. As it turns out Linux cares very much. Using the bottom port allowed normal boot without crashing xserver.

I also installed the Nvidia drivers as per tommcd's link with a few tweaks as I have a VIA integrated Chrome chipset, and not an Intel. The drivers seem to be working great, and the Nvidia Xserver config graphical editor is nice.

---

