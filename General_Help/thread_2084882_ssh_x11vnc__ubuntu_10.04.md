---
title: "ssh x11vnc  ubuntu 10.04"
date: 2012-11-16
forum: General Help
---

### Post by klein de usa on 2012-11-16
hi 

it has been a while since i have set up ssh/vnc/ubuntu 10.04 ssh is working fine what i did was 

sudo apt-get install x11vnc

i start the ssh connection to the computer with the server like this 

ssh -L5900:xxx.xxx.xxx.xxx:5900 [email]user@xxx.xxx.xxx.xxx[/email]

then once logged into the ssh server i start the x11vnc server like this 

sudo x11vnc -xkb -ncache 10 -display :0 -usepw -q

then i get the standard 8 -10 paragraphs of it failed then some possible causes so i installed the standard xorg.conf files i have that i have used many times before and it still failed i changed the driver from vesa to fbdev cause that is what fail safe x server uses to fall back on still the same thing.

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection

Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1280x1024"
EndSubSection
EndSection

Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection


has something changed or am i missing something i followed my notes and double checked them any ideas ?

---

### Post by klein de usa on 2012-11-16
ok 
so i forget things lol 

GRUB_CMDLINE_LINUX="nomodeset"

[http://ubuntuforums.org/showthread.php?t=1452600&page=3]("http://ubuntuforums.org/showthread.php?t=1452600&page=3") post #24

---

