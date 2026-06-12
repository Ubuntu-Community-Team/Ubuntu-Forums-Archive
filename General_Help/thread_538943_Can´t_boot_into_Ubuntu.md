---
title: "Can´t boot into Ubuntu"
date: 2007-08-30
forum: General Help
---

### Post by gakna on 2007-08-30
Hi everybody! sorry if am too explicative but i am new to ubuntu. After a lot of problems i managed to reconfigure my ATI Radeon 9250 and have 3D acceleration. Then i installed compiz fusion and worked fine. Then i installed the unofficial plugins: "compiz-fusion-plugins-unofficial" in order to see the 3D effects buy they didn´t work so i disabled them in the Compiz Manager. Then i installed some desktop themes (T-ish for Clearlooks and OSX iconset, and a bacground for the desktop and downloaded an icon theme: Innex which i didn´t install), and tried to connect and do a hotsync with my PDA sony clie but Ubuntu didn´t recognize it so i tried to configure the PDA program that comes with Ubuntu and didn´t know how so i left it (i might have change some settings in that program but don´t remember which). Ubuntu was working fin other than that. Next day when i tried to boot into ubuntu i saw the Ubuntu bar and then...black, nothing...couldn´t get into the X. I got into recovery mode and put: "sudo /etc/init.d/gdm restart" and could enter!!!. When it opened showed me an error: "Failed to initialize HAL", but other than that everything worked, even compiz fusion. I restarted and could enter again but as i shut down same black screen again. I tried the command "sudo /etc/init.d/gdm restart" in recovery mode again but this time didn´t work, neither to reconfigure the xorg.org, nor nothing, i can´t get into the X. Yesterday i tried: "sudo dpkg-reconfigure gdm" and then "startx" and worked, i restarted and worked again with the same error. But again, as i shut down couldn´t get in again and the command didn´t work anymore. Strange...and more for a newbie...Any ideas??? believe me i searched and tried everywhere...Thanks in advance to everybody...:)

---

### Post by nitro_n2o on 2007-08-30
you have probably missed your system enough for now :) you can solve this (it's compiz problems NOT ubuntu), but i'd suggest that you do a clean install... 
this is life you live you learn... 
have fun :)

---

### Post by gakna on 2007-08-30
Ok, i get it...one question though (since i am new to it) when i reinstall from the live CD, in the part of the installation where it offers me to partition the disk, how can i make Ubuntu to reinstall in the same partition that Ubuntu created the first time so i can keep double booting?
Thanks!!

---

