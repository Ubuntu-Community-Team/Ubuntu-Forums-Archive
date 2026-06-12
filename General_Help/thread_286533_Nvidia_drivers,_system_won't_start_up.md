---
title: "Nvidia drivers, system won't start up"
date: 2006-10-27
forum: General Help
---

### Post by siplus on 2006-10-27
Hey, i've actually had this kind of problem before, but it is definately more severe right now.

I had just installed 6.10 over my dapper install, and finished setting it all up, when I decided to install the nvidia driver.

I installed the nvidia-glx from synaptic and ran the script that changes xorg.config that comes with the nvidia package.

After I rebooted, X failed to start and I received the message stating that there was an error and gdm could not start. I went to a console and changed the /etc/X11/xorg.conf, except instead of changing it like usual where I change "nvidia" to "nv" i tried to comment out DRI module. Now it won't boot! it leaves the booting splash screen and insists on checking the mounted harddrives for integrity and just stops. I tried in the failsafe option given in the grub menu and it stops at the same place.

so, in short: 1) is there a way to restore the usability of the system without a reinstall?
2) Is there a way to correctly install the nvidia graphics driver?

---

### Post by John.Michael.Kane on 2006-10-27
logout then hit ctrl f1 

sudo nano /etc/X11/xorg.conf change nvidia to vesa 

ctrl x and Y ctrl m 

type startx 


Heres a guide

nvidia-glx this should still be installed leave it

run:
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop

paste this:
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```

save the file

sudo gedit /etc/X11/xorg.conf change vesa to nvidia

log out,and reboot the machine 
ctrl backspace

the nvidia logo will pop up for a sec then your asked to log in.

---

