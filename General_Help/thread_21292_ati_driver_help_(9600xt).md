---
title: "ati driver help (9600xt)"
date: 2005-03-21
forum: General Help
---

### Post by Hidden.Elf on 2005-03-21
I have installed the drivers as directed in wiki, but the opengl seems not to be working properly... after installing, i ran supertux w/ opengl to test this, and i was getting about 1fps... can anyone help me? thanks :-)

---

### Post by Hidden.Elf on 2005-03-21
i also checked with other opengl programs... no luck :(

---

### Post by Bicet on 2005-03-21
[QUOTE=Hidden.Elf]i also checked with other opengl programs... no luck :([/QUOTE]
 Have you changed ati to fglrx?

---

### Post by Hidden.Elf on 2005-03-21
yep... still didn't work :(

---

### Post by Bicet on 2005-03-21
[QUOTE=Hidden.Elf]yep... still didn't work :([/QUOTE]
 Is fglrx loaded on your modules?

Try 

sudo gedit /etc/modules

and add fglrx at the end

---

### Post by emuman on 2005-03-21
Look in you '/var/log/Xorg.0.log' for error messages. I guess 'fgrlx' could not initialise AGP. 
The [Radeon FAQ](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_agpenodev) explains the problem.
Try to remove 'fgrlx' from '/etc/modules' and change  Option 'UseInternalAGPGART' to 'no' in your 'xorg.conf'. The ati driver will use the external AGP driver from linux kernel.

---

### Post by taki on 2005-03-22
Okay, I have the same screen rez problem.

I'm running Hoary on my x86 machine. I've installed xorg. I've changed ATI to fglrx, I've also added it to modules. When I go to edit my XF86Conf-4 file, I discover I don't have one. It's not in /etc/X11. It's nowhere. I've installed all the xorg packages.

What haven't I done?

---

### Post by kb00heda on 2005-03-22
Is there any such file at all? I only have /etc/X11/xorg.conf. Believe it has replaced the old XF86Conf-4-file. Try and modify the former (that is "xorg.conf") instead.

/David

---

### Post by dewey on 2005-03-24
[QUOTE=taki]Okay, I have the same screen rez problem.

I'm running Hoary on my x86 machine. I've installed xorg. I've changed ATI to fglrx, I've also added it to modules. When I go to edit my XF86Conf-4 file, I discover I don't have one. It's not in /etc/X11. It's nowhere. I've installed all the xorg packages.

What haven't I done?[/QUOTE]

Instead of using /etc/X11/XF86Conf-4 to edit, try /etc/X11/xorg.conf

---

### Post by Krpano on 2005-03-25
I have an ATI 9800 Pro...and this is making my life a hell....
im almost giving it up....

---

### Post by Strider on 2005-03-25
For you guys having problems with fglrx/ATI, check out the following post I posted on another forum:

[http://m6n.ath.cx/forum/viewtopic.php?t=382](http://m6n.ath.cx/forum/viewtopic.php?t=382)

This is specifically for compiling the fglrx module and not using the one from the repository.  My experience has been that when I compile it, I get better frame rate.

Good luck! 

PS. This was once a MAJOR issue for me but you have to keep hacking at it.  One of the few things you'll come across that may give you a little hiccup but once you get it working, you'll feel much better! :)

---

### Post by bobalamer on 2005-03-26
Hi everyone,
i also have an Ati Radeon 9800 pro + Sis 746 AGP chip  and had the some difficulties .
Now it's running fine with 3D.
So i'll recap everything in that post.
First the needed package :

xorg-driver-fglrx

fglrx-control (optional i think. it gives you just the ati panel control)

xorg-driver-fglrx-dev (optional i think also)

linux-restricted-modules-k7 
K7 is because i have a K7 so choose the one matching your compute rbut also saying in the description :
"This package will always depend on the latest restricted modules available"

Linux kernel image on AMD K7 
Same logic as above choose the package that fits you best and also the generic one one saying "This package will always depend on the latest kernel image available"

install the packages the way you like it. Synaptic worked fine for me.

Configuring :

First make a copy of your actual xorg.conf so that you can at least restore the original settings if needed.

in the console type
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.save

open with a sudo the xorg.conf
in the console type :
sudo gedit /etc/X11/xorg.conf
find the following line :

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)" 

the identifier may of course be different according to your video card.
change the  Driver  "Ati" to  Driver  "fglrx"

In my case it was'nt enough the Ati driver was loaded but i had no 3D.
DRI was not possible because 'fgrlx' could not initialise AGP. 
So check your /var/log/Xorg.0.log

I have a SIS AGP chipset that's the reason why i have to use the Agpgart from the kernel and not from Ati driver.
So i had to to add in the  Section "Device" of the /etc/X11/Xorg.conf the following option :
Option "UseInternalAGPGART"         "no"

Concerning the etc/modules file :
I have no flgrx in it. Maybe it's needed when you  use the Ati internal Agpgart provided by the driver but as it not my case i do'nt know.



now when i type fglrxinfo i get :
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

 :) 

PS : If you want to know the various option of the fglrx driver use fglrxconfig.
in a console type :
sudo fglrxconfig
answer the question on the screen. The script will write the /etc/X11/XF86Config-4 file.
It's there that i did get the Option "UseInternalAGPGART"         "no"

Best regards Bob a lamer  ;-)

---

### Post by antidrugue on 2005-10-09
You did your homeworks Bob!

Pretty complete setup.

For more details/help, I suggest:

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)

Or, "advanced" users can check out : [http://www.stanchina.net/~flavio/debian/fglrx-installer.html](http://www.stanchina.net/~flavio/debian/fglrx-installer.html)
It's more Debian related, but still it ressemble Ubuntu in many ways.

---

