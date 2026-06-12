---
title: "Ubuntu OS or Windows OS boot window not centered on screen!!"
date: 2014-02-25
forum: General Help
---

### Post by stephen26 on 2014-02-25
When I start up I have the purple screen with the info for selecting Ubuntu OS or Windows OS, The issue is that the left side is off the screen and, I would like to have it in the screen so it can be read fully, at the moment all I can do is hope that I select the right one blindly.

I would like some feed back if anyone has had this happen and how they fixed it.
Thanks.

SteveO 				**[COLOR=#000000][/COLOR]**[COLOR=#000000][/COLOR]

---

### Post by bcschmerker on 2014-02-25
What type of display unit are you using?  Certain types of display units, e.g. a 26" RCA® flat-screen TV (native resolution: 1280x720) that I am using as part of an Ubuntu® GNOME® 14.01a2 test rig, have an inherent tendency to offset the entire display image from HDMI.  Proprietary X-servers such as the nVIDIA® GeForce® Software (packages: nvidia-*, nvidia-*-settings) and Advanced Micro Devices® Catalyst™ Control Center™ (packages: fglrx, fglrx-amdcccle), can compensate for this; not so in most cases the open-source X.org Video Servers.

---

### Post by nihao123456ftw on 2014-02-25
Hello Stephen26,

I'm sorry that I don't know a proper solution for this, but a possible workaround that might work is to change the boot order in the purple screen at startup

Try making your windows OS as the second option and linux as the first option or vice versa, so you know all you have to do is press the down arrow key once to choose either one of the oses

[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order) [see Eliah Kagan's answer]

basically just try running: "sudo gedit /boot/grub/grub.cfg" and then cut and paste the "###BEGIN [stuff]### menuentry { [stuff] } ###END [stuff]###" to move the booting order
fgrep menuentry /boot/grub/grub.cfg prints the boot order of your system currently by the way

---

