---
title: "ATI Driver Problems"
date: 2006-11-27
forum: General Help
---

### Post by jsmidt on 2006-11-27
I followed the installation instructions from: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

But get this error:

dave@N216ESC-2:~$ fglrxinfo 
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)


Here is my card:

dave@N216ESC-2:~$ lspci |grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc RV370 5B62 [Radeon X600 (PCIE)]
01:00.1 Display controller: ATI Technologies Inc Radeon X600(RV380)

Anybody know what the problem is and what I can do about it?  Thanks.

---

### Post by rbmorse on 2006-11-27
Open a terminal window and try this:

sudo aticonfig --initial

---

### Post by CowzRule on 2006-11-27
Do you have the following at the bottom of your xorg.conf file```
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
```If not, add it to the very bottom, reboot then run "fglrxinfo" to see if it's fixed.
In case you need to know how to edit your xorg.conf file, in the terminal type```
sudo gedit /etc/X11/xorg.conf
```
Hope this helps :)

Just some friendly advice here; it's good practice to post a copy of your xorg.conf file when seeking advice about video card problems. Most video problems arrise from miss configuration of that file.

---

### Post by jsmidt on 2006-11-27
Thanks guys, your advice helped

---

### Post by strabes on 2006-11-27
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

---

