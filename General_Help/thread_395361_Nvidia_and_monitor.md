---
title: "Nvidia and monitor"
date: 2007-03-28
forum: General Help
---

### Post by MadMac on 2007-03-28
Howdy!

Okay, I am running Ubuntu Edgy (without Beryl) on a 3.20Ghz CPU with 1024 RAM, a CTL (Computer Technology Link) 7DLN monitor and a Geoforce4 MX440 with AGP8X video card.

What I am wondering is if the Nvidia *has* to be available/show up in the list when I do the update bit?  I have the "nv" but no "nvidia" in the list to choose.  Also, when I loaded up some of the files for the video card from Synaptic it made some of the screensavers (specifically "Atunnel") not work.  It is set on "vga" and seems to work fine, though I haven't had the chance to try out the 3D bit, yet.  Oh, and the xorg.conf file does show the Nvidia card, monitor and resolution correctly.

==========================================

Xorg:

Section "Device"
	Identifier	"Nvidia"
	Driver		"vga"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"CTL 7DLN"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Nvidia"
	Monitor		"CTL 7DLN"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"

======================================

Anything I should be worried about? :-k

Thanks!

---

### Post by profXavier on 2007-03-28
First, backup your xorg.conf (in /etc/X11), then you want to run nvidia-xconfig, then you want to do nvidia-settings. Do them both as sudo, as they add/edit your xorg.conf.  This should give you the correct settings you want your video card to use.

---

### Post by MadMac on 2007-03-28
> **profXavier said:**
> First, backup your xorg.conf (in /etc/X11), then you want to run nvidia-xconfig, then you want to do nvidia-settings. Do them both as sudo, as they add/edit your xorg.conf.  This should give you the correct settings you want your video card to use.

Thanks for the quick response!!

Sorry, but I am still too much of a noob to get the gist of how to do those updates.  Mind phrasing them out for me?  I appreciate the help!

---

### Post by MadMac on 2007-03-28
Okay, I figured it out - I had to install the two things and then run them with "sudo" from a terminal.

i.e.: open a terminal and enter "sudo nvidia-xconfig" and then "sudo nvidia-settings".

Worked like a charm!

Now, if I can just figure out how to get away from this grayish-brown color backgroundish type thing I will be cooking with gas!  :)

---

### Post by MadMac on 2007-03-30
Alrighty.

I managed to get the drivers/programs loaded, and then got the ever-faithful "Xserver cannot be loaded, do you want to see the dialogs to see what happened".  Took a while, but I managed to get it back up and running.  Why does the Nvidia setup cause so much damage?

Now, can anyone tell me why the drivers/programs for loading Nvidia drivers causes almost none of the default screensavers to display?

Also, I found out that the color bit was merely a monitor going bad.  No biggie, I have plenty stashed around.  Heh.

Thanks!

---

### Post by profXavier on 2007-03-31
Ok, lets go over this again.

You WANT to have your nvidia driver loaded (in your /etc/X11/xorg.conf) not the nv, but ubuntu will work just fine with nv instead.

Now, when you get the error: "Xserver cannot be loaded, do you want to see the dialogs to see what happened" this is happening because you do not have the "nvidia" driver, in that case, you can edit your xorg.conf and change the driver back to "nv"

Next, consult the [Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") and get the latest nvidia drivers (do a search for nvidia, there are only a few on the entire page). Now once you get the nvidia drivers, you want to run both nvidia-xconfig AND nvidia-settings.

The should have a basic setup, NOW, if you want to run Beryl, you need to get it using Synaptic first.  Then once you have it installed, you want to add a few lines into your xorg.conf:

Section "Device"
# USED for Beryl
    Option          "TripleBuffer" "true"

Section "Screen"
# Enable 32-bit ARGB GLX Visuals -- FOR Beryl
    Option "AddARGBGLXVisuals" "True"

Ok, that should get you setup. NOW the bonus:

open a shell in ~ (users home dir)
nano .bashrc (then scroll to the bottom)

-- add the next three lines after this line into that file, then save it, exit your shell
# USER DEFINED ALIAS

alias xo='sudo nano /etc/X11/xorg.conf'

When you have this added, you can just type 'xo' into your shell.  You will be prompted for your password (sudo), enter it, then you can edit your xorg.conf.

If you want to be really creative, I also created another alias which backup the current xorg.conf, so its not lost:

alias xob='sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup'
-- execute this in the shell by typing xob (b for backup)

That should get you started down the road to Ubuntu, welcome, and sit back and enjoy the ride...

---

