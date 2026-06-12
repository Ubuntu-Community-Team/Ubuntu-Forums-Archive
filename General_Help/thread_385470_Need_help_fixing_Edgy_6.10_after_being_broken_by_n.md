---
title: "Need help fixing Edgy 6.10 after being broken by nVidia driver"
date: 2007-03-15
forum: General Help
---

### Post by iindigo on 2007-03-15
Hi,

I recently installed a new version of the nVidia driver for my graphics card with Envy. After installing it and rebooting, X fails to start, throws me an error message, and then drops to a blank screen with a blinking cursor. I would normally be able to fix this through the command line, but the screen is completely blank and not even a prompt is appearing.

Any ideas on how to fix this? Thanks!

---

### Post by fragos on 2007-03-15
reboot the system and take the second choice in the grub menu.  If my memory serves me correctly it will be labled for recovery.  It will start you in command mode with root privleges.  It sounds like from there you will be OK.  The most stable way to get 3D Nvidia graphics is to install nvidia-glx with Synaptic.  Most problems with nvidia come from using software not in the Ubuntu repositories to install drivers.

---

### Post by iindigo on 2007-03-15
> **fragos said:**
> reboot the system and take the second choice in the grub menu.  If my memory serves me correctly it will be labled for recovery.  It will start you in command mode with root privleges.  It sounds like from there you will be OK.  The most stable way to get 3D Nvidia graphics is to install nvidia-glx with Synaptic.  Most problems with nvidia come from using software not in the Ubuntu repositories to install drivers.

Thanks for the help!

I've run into another problem, however. During the boot process, when I'm told to press Escape to enter the GRUB boot menu, pressing escape has --absolutely-- no effect. Is the problem caused by the fact that I'm using a USB keyboard? I have a PS/2 keyboard, but I'd like some confirmation before I dig it out.




Thanks again!

---

### Post by kpkeerthi on 2007-03-15
My USB keyboard works when I'm in GRUB. But just incase, why don't you try with your PS/2 keyboard to be sure?

And... when you are in console... just run envy again... and choose 'Uninstall nvidia driver' option... Then edit your xorg.conf and change "nvidia" to "nv". That will atleast gets you to the X.

---

### Post by fragos on 2007-03-15
On my system, GRUB menu comes up by default.  I believe that controlled by a parameter in the /boot/grub/menu.lst file.  As to the keyboard and USB there may be a BIOS parameter for that.  Most USB keyboards and mice ship with a PS2 port adapter which would be the easier way.  I use my USB keyboard with one to make a USB port available for another use.  Linux doesn't seem to care one way or the other.  My keyboard is backlit and I was surprised to see that the backlight still worked over the PS2 adapter.

---

### Post by iindigo on 2007-03-15
Well, I got the initial problem resolved. I removed the new driver and restored a backup copy of my old x.org file.

The networking is borked now, however. The config is exactly the same as it was pre-install, but now it acts like it's getting nothing at all from the direct Ethernet connection it has, and I cannot do anything that requires the internet.

Any idea as to what is going on now?

---

### Post by fragos on 2007-03-15
System-> Administration-> Networking and make sure the wired connection is checked to be active.  Another thing you can do is to activate the Network Monitor applet.  It gives you a handy activity icon which if you click it will show you the Connection name which should be eth0.  The support tab will give you a look at IP configuration.

---

### Post by iindigo on 2007-03-16
> **fragos said:**
> System-> Administration-> Networking and make sure the wired connection is checked to be active.  Another thing you can do is to activate the Network Monitor applet.  It gives you a handy activity icon which if you click it will show you the Connection name which should be eth0.  The support tab will give you a look at IP configuration.

In Networking, the ethernet connection is active and appears to be fine.

As for the Network Monitor applet, I didn't install that before I lost the internet connection on the PC...

---

### Post by abba567 on 2007-03-16
I have to same problem with my graphics drive, it stopped working after i did an automatic sotfware update. i can get into the command input thingy how do i fix it?


thanks

tony

---

### Post by abba567 on 2007-03-16
please someone must have a clue please please please

---

### Post by fragos on 2007-03-16
abba567,

Rule of thumb is that when X fails to start after an uprade says the place to get things working is /etc/X11/xorg.conf. Scandown until you see something like the following:

Section "Device"
	Identifier	"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

If you hava an Nvidia graphics card or mobo chip set, change Driver "nvidia" to "nv".  nv is an open source driver for your card that only supports 2D.  Its very stable.  Another acceptable choice would be "vesa" whic is the general purpose drive that works with all VGA cards.  Xorg.conf has root permissions so in command line type "sudo nano /etc/X11/xorg.conf".  If password is asked for use your personal one.  Thi sis a very basic screen oriented text editor whose commands are Ctrl characters shown at the bottom of the page.

---

