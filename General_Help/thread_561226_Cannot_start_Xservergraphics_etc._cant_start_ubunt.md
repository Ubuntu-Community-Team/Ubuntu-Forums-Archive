---
title: "Cannot start Xserver/graphics etc. *cant start ubuntu*"
date: 2007-09-27
forum: General Help
---

### Post by Duranxl on 2007-09-27
ey all!

I tried installing wubi today but i get this xserver error, that it cannot load the GUI. Then nothing happens, i can choose to see the error log or reboot and get the same thing.

Im on a vostro 1500 laptop, nvidia 8600M GT and core2duo.
Ubuntu worked fine (not wubi though) on my older ti4200 desktop!

Any help (none of the other threads could help me out)

thanks

edit: the error is ""Failed to start the x server (your graphical interface). It is likely it is not set up correctly."

---

### Post by Duranxl on 2007-09-27
nvm i found out that there's no nvidia driver for my 8600GT yet so it couldnt display the widescreen res.
//sudo apt-get -y remove UBUNTU

---

### Post by xcapepr on 2007-10-01
Ill try to re-use this thread... I have a Dell M4300 with the Quadro M360 and the high rez screen (1920x1200)

I got the driver off Nvidia's Site (Version: 100.14.09) that lists compability. It also lists compability with your hardware Duranxl!

I can get into Ubuntu by command line. Is there any way to load the driver via command line or can the machine be booted with a generic driver?

If I can get into the GUI I can figure it out... but for now... HELP!

EDIT*

When I try to open the xorg.conf file to see it, I can CD into /etc/ but when I try to CD to /etc/X11 it says "no such file or directory", shouldn't this file exist?

---

### Post by xcapepr on 2007-10-02
Ok sere are the pics of the screens:

First I'm greeted with the X server error :(

[[IMG]http://www.xcapepr.com/images/DSC01316.JPG[/IMG]](http://www.xcapepr.com/images/DSC01316L.JPG)
The output is:

[[IMG]http://www.xcapepr.com/images/DSC01313.JPG[/IMG]](http://www.xcapepr.com/images/DSC01313L.JPG)

Then this pops up. The detailed output contains too much info to post it here:

[[IMG]http://www.xcapepr.com/images/DSC01318.JPG[/IMG]](http://www.xcapepr.com/images/DSC01318L.JPG)

***I cant even get in with the Live CD... I get this error... it just stays there! :confused:

[[IMG]http://www.xcapepr.com/images/DSC01321.JPG[/IMG]](http://www.xcapepr.com/images/DSC01321L.JPG)

Any help appreciated! :mad:

---

### Post by ago on 2007-10-02
Look for guides on how to install drivers for your particular card

---

### Post by xcapepr on 2007-10-02
I did look for guides... again if I had the GUI I can figure it out.

I tried the sudo apt-get nvidia-glx thing I read on the guide but it says that the package is unavailable or has moved... is there any way the GUI can be loaded with a generic driver a la "safe mode"?

The guide for the binary driver doest list any command line only way to install the driver.

---

### Post by ago on 2007-10-02
sudo dpkg-reconfigure xserver-xorg

as for the driver make sure that the restricted repository is enabled (/etc/apt/sources.list) and that you have an internet connection working

---

### Post by xcapepr on 2007-10-02
Ok, I ran the command mentioned and reconfigured using the default NV driver with a rez of 1680x1050 and restarted GDM (sudo GDM) and got the same error again.

I was unsure of the Video card identifier so I left it on the default PCI:1:0:0. I did the lspci command but got a big list that I couldnt scroll.

Is using the generig NV driver my best bet?

How would you resolve this ago?  

I'm a Linux n00b.. im sure you can tell :)

---

### Post by ago on 2007-10-02
vesa is the best :P

---

### Post by xcapepr on 2007-10-02
Woo got GUI, vesa dd the trick... ty!

---

### Post by DaEarl on 2007-10-03
Hi!
I get the same error. What options do we have? 

"...Restart GDM when configured correctly"

How to configure it correctly?

ASUS laptop
turion64
ATI HD 2600
1024 ram

---

