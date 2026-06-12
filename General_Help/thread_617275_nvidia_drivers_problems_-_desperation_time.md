---
title: "nvidia drivers problems - desperation time"
date: 2007-11-19
forum: General Help
---

### Post by NitrOuS on 2007-11-19
First of all I hope I post in the right section...I want help with my feisty cause I' m completely desperate. I'll try to describe the problem as well as I can to make sb understand my problem and help me fix it. Moreover I know things about computers but I'm not a linux guy, and ubuntu is the first linux I installed in my pc two years ago. 
I was trying to setup my feisty and I decided to install the latest nvidia drivers for the nvidia site. Through the search menu of the nvidia site I downloaded the drivers from the following link: [nvidia]("http://www.nvidia.com/object/linux_display_ia32_100.14.19.html")
I ran the chmod +x command to make the file executable.After some search I found out that I had to stop the Xserver in order to install the drivers. So I pressed Alt-Ctrl-F1, I logged in and I executed:
```
sudo /etc/init.d/gdm stop
``` The xserver as shown on my screen was stopped and then I executed ```
sh NVIDIA....pkg1.run
``` to enter thew installation. The installation was completed successfully I executed ```
sudo /etc/init.d/gdm start
``` and the xserver started, the nvidia logo was shown and the things seemed to be fine. After some updates I rebooted my pc and then a msg appeared telling me that the xserver wasn't configured correctly and that I had to reconfigure xserver. So I run ```
sudo nvidia-install --uninstall
``` to uninstall and the drivers were uninstalled. Then I took a look at xorg.conf file and I saw that if I wanted to reconfigure the xserver I had to execute ```
dpkg-reconfigure -phigh xserver-xorg
``` and I did so. The things again were fine. But as a stubborn I wanted the nvidia drivers to be installed! So I did the same things I had once again problems but now I can't login because even though  I listen to the drum sound of the login screen the screen is out of scan range and I can't see a thing! I tried to press alt-ctrl-F1 for the command line but the letters on the screen are not visible, they were deformed! What can I do in order to have nvidia drivers but no problems? How can I start without xserver reconfigure the nvidia drivers and then restart xserver ? PLEEEEEEEEEEEEEEAAAAAAAAAAAAAASEEEEEEE HEEEEEEEEEEEELP ME!

:cry::cry:[-o<[-o<:frown::frown::(:(

---

### Post by Qwerty_ on 2007-11-19
I would of just installed the restricted drivers to start off.

System>Administration>Restricted Drivers Manager.

However you need to get something visible to start off this proccess.

Try booting into recovery mode and see if that will let you get something visible, then try the restricted drivers.

---

### Post by atlfalcons866 on 2007-11-19
try using envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

this helped a lot when i was having problems with my old nvidia tnt2 16 mb ram.O:)

---

### Post by NitrOuS on 2007-11-19
After hours and hours of working on this problem I decided to make a clean setup of ubuntu and handle things differently. I made all the updates-upgrades, I upgraded to 7.10 and after that I installed Envy as you told me and I saw in other threads. Now all work fine. Hope it continues! Thanks all you guys who tried to help me.

---

