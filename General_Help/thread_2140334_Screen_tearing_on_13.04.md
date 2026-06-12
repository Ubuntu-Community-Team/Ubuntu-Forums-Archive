---
title: "Screen tearing on 13.04"
date: 2013-04-29
forum: General Help
---

### Post by Naygral on 2013-04-29
This problem is best viewed in either games or Flash videos, I am getting screen tearing in Lubuntu 13.04. This is based on a newly installed distro without any added programs (only updates).

Graphic Card: GeForce Nvidia 7900 GTX
Driver: NVIDIA binary Xorg driver, kernel module and VDPAU library from nvidia-304 (proprietary, tested)

(I have the exact same problem on the Open Source driver, and the two other Drivers from Nvidia)

If further information is needed, you are welcome to tell me so. Otherwise I would be very happy if anyone could help me find a solution for this problem!

---

### Post by pqwoerituytrueiwoq on 2013-04-29
make sure hardware acceleration is disabled in flash

---

### Post by Naygral on 2013-04-29
> **pqwoerituytrueiwoq said:**
> make sure hardware acceleration is disabled in flash

Thank you for the response, unfortunately that did not work for me. Even with the Hardware Accelerator disabled, I get Screen Tearing.

---

### Post by pqwoerituytrueiwoq on 2013-04-29
This is not a fix, but may work as a workaround
[http://pastebin.com/HU7zdSDC](http://pastebin.com/HU7zdSDC)
save this to /usr/local/bin/flash-video
```
sudo wget http://pastebin.com/raw.php?i=HU7zdSDC -O /usr/local/bin/flash-video
```
pause the video (change playback quality if using youtube)
open a terminal and run [FONT=courier new]flash-video[/FONT]
if you would prefer a click-able icon run this this will create one
```
sudo mkdir -p /usr/local/share/applications/;echo -e "[Desktop Entry]\nVersion=1.0\nType=Application\nName=Play Flash Videos\nComment=Allows you to easly play flash videos in video players\nExec=flash-video\nIcon=application-x-flash-video\nPath=\nTerminal=false\nStartupNotify=false\nCategories=AudioVideo;Player;Video;\nGenericName=Play Flash Videos" | sudo tee /usr/local/share/applications/flashVideo.desktop
```
menu -> multimedia -> Play Flash Videos

---

