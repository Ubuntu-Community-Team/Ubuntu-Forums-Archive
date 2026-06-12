---
title: "Error parsing the config file"
date: 2007-04-21
forum: General Help
---

### Post by Daemian on 2007-04-21
I am fairly new to ubuntu and i wanted to install beryl on ubuntu 6.10 edgy.  I used these instructions : [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)
these instructions told me to edit alot of files in gedit (which i did) but after i restarted my computer i recieved this error:

**failed to start the x server (your graphical interace) It is likely that it is not set up correctly. **

It then asks me if i want to diagnose the problem and i pressed yes.

then it showed me another error:

**Parse error on section 149 of section ServerLayout in file /etc/x11/xorg.conf "EndSectionSection" is not a valid keyword in this section. problem parsing the config file. Error parsing the config file. Fatal server error: no screens found**

i would know how to edit it in gedit but i cannot access the program even when i type it into the terminal (which i'm brought to after the diagnosis.) 

Please Help!!!

---

### Post by jtraub on 2007-04-21
Dont' worry. You can not use gedit, becuase x server doesn't running.
install vim with
```
sudo aptitude install vim
```
Then type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo vim /etc/X11/xorg.conf

```
type "g" and "149" and then press Enter
press "i" and edit line "EndSectionSection" to "EndSection"
press ":wq"
```
startx
```

---

### Post by Daemian on 2007-04-21
thanks, that problem is fixed but now another one popped up. In the diagnosis screen it is written:

[B](==)using config file: "/etc/X11/xorg.conf"
(EE) No devices detected.

Fatal server error no screens found.[/B]

---

### Post by Eric Layne on 2007-04-21
I just had this exact problem and am now able to correctly start my machine thanks to jtraub's advice and the instructions found [on this page.]("http://ubuntuforums.org/showthread.php?t=410400&highlight=restore+backup+xorg.conf")

My troubles started in the same exact manner: following a beryl installation guide found [here.]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"). I added the line 'InputDevice        "Synaptics Touchpad"' to xorg.conf, and Xserver literally broke. Kinda scary.

Edit: The above mentioned beryl installation guide [found here]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon") works properly. I am using a ATI Radeon 9550 which has only experimental 3D acceleration.

---

### Post by Daemian on 2007-04-22
thanks, i followed those instructions on beryl and installed it. but now i get an error when i run the command "beryl" it gives me this:
[B]
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options
Not a JPEG file: starts with 0x3c 0x21[/B]

and now my windows have no window themes or buttons.
thanks.

---

