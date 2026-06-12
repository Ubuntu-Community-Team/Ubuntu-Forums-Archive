---
title: "HELP COmPIZ"
date: 2006-12-02
forum: General Help
---

### Post by themerchant on 2006-12-02
I used this guide [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
to Install compiz, on my computer. I use edgy obviously. I installed it, but I didn't put to work on setup. To try compiz out, I told terminal to run it on my desktop, and suddenly all my menu bars disappeared and such, so I decided to restart the computer. I realized that during the installation I had edited some graphical system files. The computer restarts and ](*,) ](*,) 
I CAN'T EVEN LOG IN. A black background, white lettered, full screen version of terminal comes up after telling me about errors in some gaphical interface setup involing "..." saying "..." is invalid, and I realized the guide said:
Make sure the glx module is loaded 
	Load	"glx"
Find this section (your values may vary) 
Section "Device"
	Identifier	"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection
Replace with the following lines, leaving the Identifier and BusID as it is 
Section "Device"
	...
	Driver		"nvidia"
	...
	Option		"RenderAccel"		"true"
	Option		"AllowGLXWithComposite" "true"
EndSection


I'm guessing I have to remove the dots, but I can't even go into my computer to do it. What should I do?

---

### Post by LLRNR on 2006-12-02
That "black background / white text full-screen version of the terminal" is in fact your means of salvation... you'll notice a "login: " prompt, just type in your username, next your password at the "Password: " prompt, and if you **have** to modify that file (xorg.conf), just use *sudo nano /etc/X11/xorg.conf*

Otherwise, try```
sudo dpkg-reconfigure xserver-xorg
```

LLRNR

EDIT - To save your file, you will have to hit Ctrl+O ( = write out = save ) and then Ctrl+X to exit.

---

### Post by themerchant on 2006-12-02
I had a feeling it would help me, but I'm not used to not having a desktop in sight, I've only been using ubuntu and terminal for around a month. I'll try that.

---

### Post by LLRNR on 2006-12-02
Nah, no need to worry, you'll only get *nano* fullscreen :D Edit out of xorg.conf what's not alright, save, exit and then try **startx**

Good luck !

LLRNR

---

