---
title: "Ubuntu Crashes on to login Screen when pulling down a maximized window"
date: 2013-04-10
forum: General Help
---

### Post by Durgol on 2013-04-10
Hi
I'm a re-beginner of ubuntu and it changed a lot. Additionally to not being able to find ways of tweaking its appearance, Ubuntu crashes on a regular basis to the login screen.
This happens as soon as, for instance chrome, a window which is maximized should be minimized by pulling down the top end of the window. 
This is not the only bug I am experiencing as I had to remove "ubuntu one" in order to prevent the same crashes. 
Before I get to the login screen I get a short black screen saying something which I can not remember because it's appearing only for a second or so.
Also after crashing to the login screen the whole session is lost which means I always have to restart all programs i used earlier.
Another problem appears when starting up ubuntu. Well it's not that big a deal but it's just not appealing. Instead of the ubuntu loading screen it looks more like my GPU has been roasted which of course is not the case. The picture is mainly purple but has some weird lines and pixels which normally would make me think my GPU is broken. But it works normally on my windows partition..
Also the GPU-Driver of nvidia has the consequence of, after installing it, having no GUI whatsoever. I had to reinstall.
I do not know if these are common problems or if it's just me. But I remembered ubuntu to be a lot better than it appears to be now. 
I also get performane issues concerning moving windows which just does not appear to work smoothly. It "lags".
I'd be glad for any help.
Thx

Edit: i got ubuntu 12.10 - 64 bit running simultaneously to windows 8.
Windows 8 is on SSD. 
Bootloader on SSD
2Tb harddrive is divided into 1.5tb windows partition and 500gb ubuntu partition.

Best regards

---

### Post by coffen on 2013-04-22
Same happens here using Ubuntu 12.10 64bit
Dunno if it has any significanse, but my install is also on SSD with /home on a separate 1GB hard drive.
Graphics card is Asus GeForce GTX 650 (nvidia chip)
I am not logged into standard unity session as I prefer using Cairo Dock session.

Actually I found Ubuntu to crash not only when pulling down maximized windows, but also in the following cases:
Dragging a windows around the screen sometimes results in a crash when releasing the mouse button after moving the window.
Switching from one workspace to another and back to the one that has a mazimized windows often results in a crash.

Edit:
Moving windows around only seems to crash LightDM if I reposition a firefox window. Moving a nautilus window around the screen does not crash LighDM.

Edit2:
I solved the problem by changing to another graphics card.
The GTX 650 caused the above mentioned crashes. After replacing that one with Asus 210 Silent (nvidia chip) the problems dissapeared.
This at least fixed it for me.

---

