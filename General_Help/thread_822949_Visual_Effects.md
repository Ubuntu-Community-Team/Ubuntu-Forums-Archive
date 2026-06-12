---
title: "Visual Effects"
date: 2008-06-08
forum: General Help
---

### Post by sagresnaw on 2008-06-08
Okay, I'm assuming that this thread has been created many times over, but I am really new to all of this and kind of frustrated.

I have a Nvidia 8600, I am using Hardy Heron 8.04 

I had a horrible time with trying to get the drivers. I was stuck with a 800x600 screen resolution, and I was able to find out how to correct it from a post here on the forums. (I forget where now)

But I can't get the Extra or even Normal features of the Visual Effects. If I'm missing any information lemme know I'll try and provide what I can. Although I have no idea on how to get any statistics or anything of the sort.

/EDIT

I guess I should also mention that whenever I go to boot Ubuntu as it's loading I get a stall at "Activation Swapfile swap".
But I just ctrl+alt+del and it continues.

---

### Post by Sef on 2008-06-08
I have the same card.  I simply went to System > Administration > Hardware Drivers to download NVidia's restricted drivers.  I have had no problem. 

Did you download them from NVidia's site?

---

### Post by sagresnaw on 2008-06-08
See, at first under my Hardware Drivers I had the nvidia, but I couldn't update, it was enabled but was "Not Active".

Visual Effects didn't work then either.

Now, I have nothing in my Hardware Drivers. I see people going to Restricted Drivers or something under the Admin list, but I don't have it.

/EDIT
Mhmm, I got the files from the site, but it was the 169.12 files I'm pretty sure.

I got the files using 
wget "link"
sudo sh "NVIDIA-Linux-x86-169.12-pkg1.run

Restarted Ubu and I got the resolution back to normal. Then this brings us to where I am now. No visual effects, and nothing in my Hardware Drivers.

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> See, at first under my Hardware Drivers I had the nvidia, but I couldn't update, it was enabled but was "Not Active".

Visual Effects didn't work then either.

Now, I have nothing in my Hardware Drivers. I see people going to Restricted Drivers or something under the Admin list, but I don't have it.

/EDIT
Mhmm, I got the files from the site, but it was the 169.12 files I'm pretty sure.

I got the files using 
wget "link"
sudo sh "NVIDIA-Linux-x86-169.12-pkg1.run

Restarted Ubu and I got the resolution back to normal. Then this brings us to where I am now. No visual effects, and nothing in my Hardware Drivers.

try running "compiz --replace" from the terminal and see what it reads. for hardware drivers you may have to enable all repositories in System/Administration/Software sources.

---

### Post by sagresnaw on 2008-06-08
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


I got that when I typed compiz --replace

and how would I enable repositories? Infact in that list where are the repositories?

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 


I got that when I typed compiz --replace

and how would I enable repositories? Infact in that list where are the repositories?

looks like your graphics drivers are not working. in the software sources, check that main, universe, restricted and multiverse repositories are on. also, you may have to tick the first four positions in the updates tab. these would be security, updates, proposed and backports. but I'm not sure if this will help, if you installed your driver manually. maybe you'll have to remove it for everything to work as it should.

---

### Post by sagresnaw on 2008-06-08
"Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

Everything is checked,and that popped up.

If I were to uninstall my drivers manually what would I have to do? (A link to another place would suffice)

So far I have to thank everyone that has helped me so far. I hope that holding my hand through all this won't push people away from helping. Haha.

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> "Could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct."

Everything is checked,and that popped up.

If I were to uninstall my drivers manually what would I have to do? (A link to another place would suffice)

So far I have to thank everyone that has helped me so far. I hope that holding my hand through all this won't push people away from helping. Haha.

the repos could be temporarily down, you can try switching to your local mirror in software sources. I dunno about removing your faulty drivers, I never installed them like you did, but could you show what's in your xorg.conf file? it's in /etc/X11. it will show your current driver.

---

### Post by sagresnaw on 2008-06-08
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Uhh, did I do that right? I got the file and opened it, I actually see nothing about a video driver. But I guess I'm not that keen on this stuff yet.

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

Uhh, did I do that right? I got the file and opened it, I actually see nothing about a video driver. But I guess I'm not that keen on this stuff yet.

it's in the "device" section. :) but it doesn't seem that Nvidia's driver is in use. I would recommend you try installing again from system/administration/hardware drivers. your repos have to be updated, mind you (from system/administration/update manager, for example, or just enter "sudo aptitude update" in the terminal). if that won't work, try this command:
sudo dpkg-reconfigure -phigh xserver-xorg
restart and try again. if that still won't work, first make a backup copy of xorg.conf, for example like this:

cd /etc/X11 && sudo cp xorg.conf xorg.conf.bck

then try pasting this into your xorg.conf file, in place of the relevant section:

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

then restart. but if you mess it up or if Nvidia driver is not installed correctly, that will screw up your graphical environment. that means you will only have access to the command line. if that happens, run:

sudo dpkg-reconfigure -phigh xserver-xorg

if that still won't let you into the gui after restart, do:
cd /etc/X11 && sudo rm xorg.conf && sudo cp xorg.conf.bck xorg.conf
if all this won't work, that means you're out of luck. you're also out of luck if I made a typo somewhere in this post. :) that's why you should try installing from system/hardware drivers, if possible.

EDIT: oh yeah, another method: install envyng-gtk, run the wizard, and let it guide you through drivers installation. that never worked for me, but it may for you.

---

### Post by sagresnaw on 2008-06-08
I tried the first thing, I'm going to restart now. But the envyng-gtk is what first fooled up my resolution haha, so I don't think I'll use Envy for a while.

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> I tried the first thing, I'm going to restart now. But the envyng-gtk is what first fooled up my resolution haha, so I don't think I'll use Envy for a while.

oh yeah! just remembered. you don't have to restart your computer every time, just press Alt+Ctrl+Backspace to restart your graphical environment. this will log you out, so don't do it with important work open or something.

---

### Post by sagresnaw on 2008-06-08
Hmm, it's a fast load anyway. No luck with the first idea.

Also, there's still nothing in my Hardware Drivers.

I'm kind of iffy to do the editing of the file, at least until you can assure me you didn't make a typo. :D

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> Hmm, it's a fast load anyway. No luck with the first idea.

Also, there's still nothing in my Hardware Drivers.

I'm kind of iffy to do the editing of the file, at least until you can assure me you didn't make a typo. :D

it's not good that there's nothing in Hardware Drivers. your card should be detected. are you sure your repositories are updated? it's also good that you're wary of modification of crucial system files. that's why you should make backups. but I know it can be stressing, if you're not used to command line. to be honest, if I were you, I'd have reinstalled the system by now and just kept away from Envy. ;) it won't take long, you know. (I hope you've created a separate partition for your home folder, if you have some stuff on your desktop you'd like to keep). but that's just me, I kinda like reinstalling. ;) apart from that, I really can't think of anything else to do in this case. good luck.

---

### Post by sagresnaw on 2008-06-08
Ok, I sort of done some fooling around. I installed(I think) something called libc header files. Then I tried installing the drivers again the way I did the first time, I exited out of the X thing using ctrl+alt+f1. Installed the driver that way, and everything actually worked out fine? I got a big splash screen saying NVIDIA so I guess I got it right.

I dunno what I did, I guess I got a beginners luck? 

I still have nothing in my Hardware drivers. 

Visual Effects work now, but when I restart I still get the swapfiles swap thing. Don't know how to fix that.

---

### Post by Grishka on 2008-06-08
> **sagresnaw said:**
> Ok, I sort of done some fooling around. I installed(I think) something called libc header files. Then I tried installing the drivers again the way I did the first time, I exited out of the X thing using ctrl+alt+f1. Installed the driver that way, and everything actually worked out fine? I got a big splash screen saying NVIDIA so I guess I got it right.

I dunno what I did, I guess I got a beginners luck? 

I still have nothing in my Hardware drivers. 

Visual Effects work now, but when I restart I still get the swapfiles swap thing. Don't know how to fix that.

glad you made it. one way or another.

---

### Post by sagresnaw on 2008-06-08
Thanks very much for the help.

---

