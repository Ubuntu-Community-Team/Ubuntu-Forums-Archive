---
title: "&quot;dpkg was interrupted&quot; Xserver Problems with update"
date: 2008-04-29
forum: General Help
---

### Post by Trampis on 2008-04-29
When I was updating this morning everything was going fine until I got the messages about problems installing xserver and xorg, the installation then closed and told me my system was unstable(!!) and I had to run 
>  dpkg --configure -a 

I searched through the forums for a fix and found this guide here  [http://ubuntuforums.org/showthread.php?t=241254]("http://ubuntuforums.org/showthread.php?t=241254") it seemed to be a similar problem albeit from a while ago. 
 It seemed to be working until I tried 
> " sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10"
 
so:
> john@dell:~/ies4linux-2.99.0$ sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
john@dell:~/ies4linux-2.99.0$ dpkg --configure -a
dpkg: requested operation requires superuser privilege


Now, I am worried that if I switch to root, the xserver will reset, crash and I will be stuck at the terminal with no access to this forum to find out what to do (all i run is ubuntu)

I also tried
> sudo apt-get remove xorg-driver-fglrx
then 
> sudo apt-get install xorg-driver-fglrx
only to get 
```
 Errors were encountered while processing:
 hal
 gnome-mount
 gnome-power-manager
 gnome-session
 gnome-volume-manager
 hal-cups-utils
 hwdb-client-common
 hwdb-client-gnome
 network-manager
 network-manager-gnome
 pulseaudio-module-hal
 sound-juicer
 update-notifier
 ubuntu-desktop
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So then I tried installing the 'xserver-xorg-core_1.0.2-0ubuntu10.4_i386.deb' manually
The pakage installer said my directories were damages so i ran
```
sudo apt-get install -f
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Now when I open package installer it tells me that there is a newer version already installed. My version is  2:1.4.1~git20080131-1ubuntu9. 

I have also tried envy, also does not work. 


 What should I do?
Should I roll back to feisty (the last version that worked well for me), if so, how do I do that?

---

### Post by mali2297 on 2008-04-29
> **Trampis said:**
> 
Now, I am worried that if I switch to root, the xserver will reset, crash and I will be stuck at the terminal with no access to this forum to find out what to do (all i run is ubuntu)


I suggest that you do as you were told, i.e., run
```

sudo dpkg --configure -a 

```
If the scenario comes true that you get stuck at the terminal, then use a text-mode web browser like **w3m** (preinstalled) to reach these forums:
```

w3m ubuntuforums.org

```
Try it out beforehand so that you know that you can use it, **Shift+h** gives you a list of key bindings.

---

### Post by Trampis on 2008-04-29
So I restarted, it did crash, so i logged in as root and did --reconfigure -a.
nothing happened, ending with still being stuck at terminal.  
So I used envy to restart the xserver without nvidia, and when I run the driver manager i am given the error 
> Sub-process /usr/bin/dpkg returned an error code (1)" 
also when running as root, ubuntu froze when i tried to quit. Probably just a symptom. 
 
So now I am running in low graphics mode with no drivers for my nvidia. 

Here is my xorg.conf if that sheds any light on anything
```
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
	Option		"Emulate3Buttons"	"true"
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
EndSection
```

---

### Post by Trampis on 2008-04-29
so i uninstalled envy, got envyng purged all the drivers from my system and then got new ones, seems to be working.
 
If anyone else has this problem go to
 [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

and get envyng.

---

