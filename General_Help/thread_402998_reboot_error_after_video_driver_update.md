---
title: "reboot error after video driver update"
date: 2007-04-06
forum: General Help
---

### Post by MeThePeople on 2007-04-06
i attempted to update my drivers using a tutorial found here 
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

i installed them fine but found the original drivers to be faster so i attempted to revert by using the method on that same site 

[edit] Revert to Xorg driver 
If (for any reason) the fglrx install fails, you can revert to the Xorg driver by executing 

sudo dpkg-reconfigure xserver-xorg

and selecting the "ati" driver, or simply restoring the previous /etc/X11/xorg.conf file, if you made a backup


unfortunatly i dident backup that file and attempted to restore it best i can by selecting the best sounding settings for my comp. upon with reboot im greeted with this error.

failed to start the x server (your graphical interface). it is likely it is not set up coorectly. would you like to view the xserver output to diagnose the problem.

followed by 2 windows with the diagnosis which was to long for me to write down. and then followed by another window which says,

the x server is now disabled. reboot gdm when it is configured correctly.

anyone have any tips on how to properly configure it?

---

### Post by r4ik on 2007-04-06
[http://ubuntuforums.org/showthread.php?p=2351383#post2351383](http://ubuntuforums.org/showthread.php?p=2351383#post2351383)

Try  #6

 Set driver to mesa,

and if you have got a visual try,

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by MeThePeople on 2007-04-06
will try and if it help i found this 

fatal server error addscreen/screeninit failed for driver 0

---

### Post by MeThePeople on 2007-04-06
ok sudo cp /etc/X11/xorg.conf~  /etc/X11/xorg.conf
gives me a unknown command error and gksudo gedit /etc/X11/xorg.conf
dosent work as i have no graphical display to run it in. when i try to boot all i can do is log into the base terminal although
sudo dpkg-reconfigure xserver-xorg does work i dont know the proper configuration although i am setting it to the best of my knowledge

ati radeon 9550
1024x768 @75htz
busid pc1:1:0:1
and i autodetect all the keyboard settings.

---

### Post by r4ik on 2007-04-06
Try,

sudo dpkg-reconfigure xserver-xorg

and try the same little bit more info here,

[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

Good luck !

---

### Post by steefjeqv on 2007-04-06
Hi,

Try this : 

sudo dpkg-reconfigure xserver-xorg

Then choose driver "vesa".

This will hopefully enable X again. Without hardware accelaration though.

Greetings,
Steven

---

### Post by MeThePeople on 2007-04-06
thanks steef that fixed it i guess the default ati driver isent compatible

---

### Post by steefjeqv on 2007-04-07
Hi,

You should also be able to use the "ati" driver.

Did you use synaptic manager when installing/uninstalling the fglrx-driver ?
If so, first check with the synaptic manager if these are removed.

Then open a terminal and type :

sudo gedit /etc/X11/xorg.conf

In "Section Device" the driver should be "vesa". Change it to "ati".
Save xorg.conf and press Ctrl-Alt-Backspace.
If you're greeted by your login screen then your "ati" driver should be working.
If, on the other hand, X is refusing to start use :

sudo dpkg-reconfigure xserver-xorg 

and revert back to the vesa driver.

By the way, as r4ik mentioned in one of his previous posts, you can use Alberto Milone's script which installs the official (closed-source) drivers from ATI.
If you're planning to do this, first check if your video card is still supported.

Greetings,
Steven

---

### Post by bigken on 2007-04-07
its easier if you use sudo dpkg-reconfigure -phigh xserver-xorg using this command only gives you the driver and resolution options :)

also have you tried [envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install your drivers

---

