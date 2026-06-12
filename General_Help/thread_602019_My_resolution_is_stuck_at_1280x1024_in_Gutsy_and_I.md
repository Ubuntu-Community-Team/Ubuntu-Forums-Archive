---
title: "My resolution is stuck at 1280x1024 in Gutsy and I can't change it"
date: 2007-11-03
forum: General Help
---

### Post by Starrfoxx on 2007-11-03
I'm not sure what happened.  Last night, I had my Gutsy install working just fine.  My resolution was set for 1024x768.  The only problem I really had was with booting up.  The login screen I think is 1280x1024, but as a result my screen is shifted to the right about 2 1/2 inches.  After I logged in, my desktop resolution would switch to 1024x768 and all would be well.

Today though, my desktop is coming up as 1280x1024 and every time I try to switch it, it won't work.  Instead nothing happens, and I go back to Screen Resolution Preferences and it's still on 1280x1024.  I'm not sure what is wrong.

I have an Nvidia 6100 graphics chip.  I don't know if I have the latest drivers installed, because I went with the "download available" version that I got when I first installed Gutsy.

---

### Post by wuziq on 2007-11-05
man this internet thing is great.

i googled for "ubuntu gutsy screen resolution stuck at 1280x1024", because i am also having this exact same problem!  i, too, want my resolution set to 1024x768.  it worked for a couple days, and now today it's not working.  i tried logging in and out, and it worked, but now it's not working again.

i have an ati radeon 9500pro.  i'm not using the restricted drivers.  i don't have visual effects on, either.  i have a dell M992 crt monitor.

any ideas?

edit:  already tried this:  [http://ubuntuforums.org/showthread.php?p=3695940](http://ubuntuforums.org/showthread.php?p=3695940)  didn't work.

---

### Post by dcstar on 2007-11-05
> **wuziq said:**
> man this internet thing is great.

i googled for "ubuntu gutsy screen resolution stuck at 1280x1024", because i am also having this exact same problem!  i, too, want my resolution set to 1024x768.  it worked for a couple days, and now today it's not working.  i tried logging in and out, and it worked, but now it's not working again.

i have an ati radeon 9500pro.  i'm not using the restricted drivers.  i don't have visual effects on, either.  i have a dell M992 crt monitor.

any ideas?

edit:  already tried this:  [http://ubuntuforums.org/showthread.php?p=3695940](http://ubuntuforums.org/showthread.php?p=3695940)  didn't work.

You need to check your /etc/X11/xorg.conf file and see if there are any unwanted resolutions listed.

You can run the reconfigure program again and manually select the resolutions you want to use rather than what is detected from the hardware.

---

### Post by wuziq on 2007-11-05
So, even though 1280x1024 is a valid resolution for my video card and monitor, I should edit xorg.conf such that only 1024x768 is available?  That seems to be avoiding the real problem/bug, whatever it is..

---

### Post by itsjustarumour on 2007-11-05
> **Starrfoxx said:**
> I'm not sure what happened.  Last night, I had my Gutsy install working just fine.  My resolution was set for 1024x768.  The only problem I really had was with booting up.  The login screen I think is 1280x1024, but as a result my screen is shifted to the right about 2 1/2 inches.  After I logged in, my desktop resolution would switch to 1024x768 and all would be well.

Today though, my desktop is coming up as 1280x1024 and every time I try to switch it, it won't work.  Instead nothing happens, and I go back to Screen Resolution Preferences and it's still on 1280x1024.  I'm not sure what is wrong.

I have an Nvidia 6100 graphics chip.  I don't know if I have the latest drivers installed, because I went with the "download available" version that I got when I first installed Gutsy.

I finally got round to installing the final version of Gutsy today, could change screen resolutions fine to whatever I wanted.  Powered off, went for dinner, came back and powered on again...  and now I'm stuck at 1600x1200!

I've been using this same PC - identical hardware, identical setup, NVidia 6800LE - for Breezy, Edgy, and Feisty and never had this problem before.

This just sucks - I really shouldn't have to edit my Xorg.conf just to change screen resolution!  Come on devs, what are you playing at??!!! :frown:


EDIT - I've also tried the fix at  [http://ubuntuforums.org/showthread.php?p=3695940](http://ubuntuforums.org/showthread.php?p=3695940) but no joy.  I've also noticed that since this problem occurred, the maximum refresh rate I can select for my monitor is 75Hz whereas it was 100Hz before.  I've also tried disabling Compiz but again no joy...  :-(  Graphics driver is just the standard NVidia one that Ubuntu automatically downloads btw.

---

### Post by Starrfoxx on 2007-11-05
I don't mind changing the Xorg file.  What part should I look for, or would it be better for me to just post the file here?

---

### Post by SteveF on 2007-11-05
I had the same problem after the latest compbiz download.  Prior to that recent download, my screen resolution would set.  Now it got stuck.  I ended up going into System->Administration->Screens and Graphics.

It showed the wrong monitor.  I changed it to my monitor and it displayed a gray popup (mostly offscreen so I could not read it).  I just hit enter and it asked if I wanted to keep the new resolution.  I said yes.  Then all of my prior resolution settings (my screen is different from another use's) all of a sudden started working again.  I did not have to go and reset them.

I think the compbiz update did something to the xorg.conf that going into Screens and Graphics cleared up.

Steve

---

### Post by Starrfoxx on 2007-11-19
I'm still a little shaky on what to actually change.  I'll post some more info.  Here's the monitor I have.  It's a GEM LCD 19" monitor.  I can't find the instructions on it.

[http://www.amazon.com/GM-190B-GEM-19-LCD-Monitor/dp/B0007V27YE]("http://www.amazon.com/GM-190B-GEM-19-LCD-Monitor/dp/B0007V27YE")

My Screen and Graphic Preferences are set at Custom 1024x768 at 57Hz. Clicking on it further I found, Generic Manufacture -- Horizontal is 31.5-48.0, and Vertical 56-65

Now my desktop comes up looking fine, but the boot screen where I log in is off center.  Sometimes it stays that way after I log in.

Here is my xorg.conf file:

# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"nvidia"
	Busid		"PCI:0:13:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	Horizsync	30-70
	Vertrefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by Starrfoxx on 2007-11-19
Oh yeah,

My graphics include an onboard 6100 Nvidia chip.  Gutsy installed Nvidia drivers, although I'm not sure which version I have.  I do know that there was an automatic update for them.

It looks like it says "Nvidia VESA driver (generic)".  Maybe that's not the right driver to be using?

---

### Post by Banacek on 2007-11-19
I have a Gigabyte GA-7VAXP (dual BIOS) mainboard with an IDE Promise 20276 RAID MBFastTrak133 Lite controller enabled as a RAID(0) array and Gusty installed on that. It has one GB of PC3200 DDR (DDR400 or at 400 MHz, I believe) SDRAM and is using an AMD Athlon (Thunderbird) 2200+ CPU (1.8 GHz normal speed). I have an ATI Radeon 9600 Pro graphics card installed into the mainboard AGP slot. I also have some sort of Radeon TV tuner card in one of the PCI slots that I haven't tried anything with yet but would like to. I don't have any of the proprietary video drivers installed but rather my system seems to be using the VESA driver. (Should I install the proprietary Radeon drivers or not and why?)



I seem to be having the same problem. Today, I tried to switch my screen resolution to 864 x 423 temporarily for something that looks better at that lower resolution. I was not allowed to do so. When I'm done with that I would like to set my screen resolution 1024 x 768 but apparently I can't do that either as I seem to be stuck with 1280 x 1024. What should I do? Will that Compiz upate that SteveF did work for my system?

---

### Post by sloxp on 2007-11-20
I wish mine was stuck on 1280x1024, instead it is stuck on 640x480.  It seems obvious that UB 7.1 has a bug in it's screen res. area.  I have an Inspiron LP 9400, and the screen res. responded to changes for about three days, and then I turned the thing off, and went to bed. The next morning I booted up, and screen res. was stuck on 640x480 and rate was stuck at 65.  I am a NUBee, but it seems that the Ubuntu Development Team needs to address this problem.  I have Feisty on my Desktop and changes to screen res. works just fine.  I think it is a software problem, rather than a hardware problem.

[email]kfbrandon@pamlico.net[/email]

---

### Post by sloxp on 2007-11-20
A lot of users are having this problem,  I think it is a software bug and not so much of a hardware problem.  I just installed UB 7.1 on a Dell Inspiron 9400, and screen res. was changeable for about three days, and then, without any input from me, it got stuck on 640x480, and is still there.  If you solve your problem, please let me know.

[email]kfbrandon@pamlico.net[/email]

---

### Post by itsjustarumour on 2007-11-20
> **sloxp said:**
> A lot of users are having this problem,  I think it is a software bug and not so much of a hardware problem.  I just installed UB 7.1 on a Dell Inspiron 9400, and screen res. was changeable for about three days, and then, without any input from me, it got stuck on 640x480, and is still there.  If you solve your problem, please let me know.

[email]kfbrandon@pamlico.net[/email]

Mine comes and goes, around one in five times I boot up my system the screen res is set to 1600x1200.  Amending the settings doesn't work, although it then fixes itself after another reboot.  Amending xorg.conf doesn't help.  I'm also not getting the right refresh rates - typically 52Hz when I should have 100Hz...

---

### Post by sloxp on 2007-11-20
It is A SOFTWARE PROBLEM.  I just rebooted my Inspiron 9400 with the live CD UB 7.04 that came with the book UBUNTU FOR NON-GEEKS, and the resolution can be changed!!!!  I think I have a live boot for UB 701, and I will try that next, and report back.

[email]kfbrandon@pamlico.net[/email]

A bug should be reported on this problem,  I do not know how!!

---

### Post by sloxp on 2007-11-20
SOFTWARE PROBLEM confirmed!!  I rebooted my Inspiron with a live CD for UB 7.1 and changes to screen res. work just fine.  The installed boot files for UB 7.1 must get corrupted or they are unstable.

Would it be safe to reinstall 7.1 on top of the currently installed 7.1,  or is there a REPAIR option?

[email]kfbrandon@pamlico.net[/email]

We need a BUG REPORTER for this problem!!!!!

---

### Post by Tyke91 on 2007-11-20
this is the "screen" section of my xorg.conf file and it works fine for me

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G72 [GeForce 7300 LE]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    SubSection "Display"
        Modes        "1680x1050"    "1440x1440"    "1440x900"    "1280x1024"    "1024x768"    "800x600"    "720x400"    "640x480"
    EndSubSection
EndSection

```i don't know why you are missing those monitor resolutions, but if you add the ones you want in, then you can set your resolution accordingly (don't use some of the higher up ones, as those are widescreen)

---

### Post by sloxp on 2007-11-20
Does our BUG RESOLUTION TEAM know about this SOFTWARE PROBLEM with the installed boot files for UBUNTU 7.1?

---

### Post by Nunu on 2007-11-20
Funny but i had this issue with 7.04. Can't remember how i fixed it but i know it had something to do with replacing Xorg and restarting X. I think I backed up my xorg.

---

### Post by Banacek on 2007-11-20
Today I did```
su root
password: <I entered my password>
dpkg-reconfigure -phigh xserver-xorg
```


It makes a backup of your xorg.conf file for you and then updates it. That seemed to clear things up for me at least for now. We'll see how it goes tomorrow.

However, when I clicked on the button to revert to the previous screen resolution I lost my mouse pointer. I eventually got it back but then whenever I clicked something it would lag out. I had to do the alt+PrintScreen +***_R_***(aising) +***_S_***(kinny) +***_E_***(lephants) +***_I_***(s) +***_U_***(tterly) +***_B_***(oring) thing for a safe reboot. That shouldn't happen so something is still very much NOT right there. For now, if a selected screen resolution isn't wanted, it's best just to accept first and then change the resolution again afterwards.

---

### Post by sloxp on 2007-11-20
It seems we need bigger guns to attack this problem (The monitors and experts with Ubuntu 7.1!  I am a NUBee and do not know how to report this BUG.

[email]kfbrandon@pamlico.net[/email]

---

