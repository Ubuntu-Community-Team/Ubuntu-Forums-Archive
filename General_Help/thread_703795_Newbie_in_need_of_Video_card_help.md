---
title: "Newbie in need of Video card help"
date: 2008-02-21
forum: General Help
---

### Post by Biciclettapc on 2008-02-21
Ok, old Dell Optiplex system I set up with Ubu for my son.  

 I am new to Ubu and Linux

The Dell is a optiplex GX110 (933mhz cpu) with on board video.  My son likes to play a few online games so I decided to upgrade the card to a little better one.  I picked up a cheap Nvidia MX400 64mb PCI card.  This system has a motherboard, daughter board config for addtional pci cards.

Initially I installed the new card and just restarted hoping Ubu would pick it up and install what it needed.  No luck......

So next I go to add/remove and installed the the legacy Nvida driver (on board graphics running), restart and no luck either.  What happens here is bios picks up the new card and posts, the first Ubu screen comes up and then it goes to the [ok] screens and stops.  Bios set to auto.

So I decide to try a fresh install from the disk with the new card installed (bios set to auto).  Disk goes to about the same spot and stops and freezes up and wont install.

So, I decide that I will tell bios to go to on board video and install the new VC.  Ubu loads.... I try installing the restricted driver and wont let me, no cards found.

Next, I keep the new VC in and once again tell bios to go to on board (options are either auto or on board) and I am able to install Ubu fresh.  Once it installs I am able to load the restricted driver and asks for a restart, which I do.  But it goes to post, Ubu first screen comes up and locks up at [ok] screen.  Oh, bios was set back to auto.  

I have d/l'd the Nvidia driver.run and its sitting on the desktop.  I am unable to get this program to load inside or outside of 'X".  This more than likely is a operator error :rolleyes:

I really would like to get this card up and running for my son.  The on board graphics are limited and for some reason it wont hold the display settings on restarts.  So its running 800x600 on a 22" LCD screen.

ANY help would be greatly appreciated.  I am new so might have to explain it real slow for me :lolflag::lolflag:

---

### Post by Rocket2DMn on 2008-02-21
Set your BIOS to auto (or even to select the nvidia card only if possible) and follow this guide to reconfiguring X:
[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
You may need to start with the open source nv driver and then select restricted drivers from within the GUI.  This is preferable to installing the nvidia drivers yourself, though sometimes it is necessary.
Having 2 cards has been known to cause problems, but we've usually been able to fix it.

---

### Post by Biciclettapc on 2008-02-21
Well, did everything in the instructions and it all seemed to accept until I restarted GUI.

I get a error message after I restart x that says something to the effect....
Fatal server error:
no screens found
xio: fatal io error 104 (connection reset by peer) on x server ":0.0" after 0 requestes (0 known processed) with 0 events remaining.

tried it 2x just in case, same error both times.

---

### Post by Rocket2DMn on 2008-02-21
That means no "Screen" section was created in xorg.conf.  Why don't you try the automatic reconfigure so at least get a GUI:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Post back after you get that and we'll procdeed.

---

### Post by Biciclettapc on 2008-02-21
Doing a clean re-install right now.  I had some weird issues before I did all the reconfig's and I thought all my attempts might have messed things up.

So sort of slow to re-install but I will try again, hopefully tonight and let you know.

Thanks for all the help!

Paul

ps:  another question, this one on a new build up I am working on.  I have a gigabyte mobo, ga-m68sm-s2 with onboard nvida 7025 graphics.  I was considering sticking a gf8400 pcie card in for better graphics (not sure if I improve much if any).  After all this with the old optiplex I wonder if its worth the hassle?  thoughts?

---

### Post by BLTicklemonster on 2008-02-21
Also, look and see if it shows the bus id for the video card as being something other than 1:5:0 (when it says no screen found) and if it does, then you'll have to manually enter what it shows when you do reconfigure dpkg. Or you can sudo nano /etc/X11/xorg.conf and scroll down to the bus id, and manually edit it from there. 

But I really don't think that's your problem.

---

### Post by Biciclettapc on 2008-02-21
reloaded Ubu with new VC in and bios set to on board (only way).  

Restart after install and change bios to auto (only other option) and hook vga to new VC.  Bios posts, Ubu begins to start and I get a blank screen.

Unable to get command prompt from here.... tried ctl+alt+f1, ctl+f1, Alt+f1 and verbal abuse to monitor.  Last made me feel good but still no results

I can get to term or command if I go back to on board and connect vga to onboard, but that sort of defeats purpose doenst it?

Thanks
Paul

---

### Post by uberlube on 2008-02-21
Did you try using ENVY to install your driver. It automatically installs the proprietary driver needed without the headaches.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Biciclettapc on 2008-02-21
No I havent, I ran across that the other night working on this but passed.

If I can get it working the other way I would prefer that, gives me a understanding of what i did and why.  

If that fails I will give it a try.

Thanks
Paul

---

### Post by Biciclettapc on 2008-02-22
Update:

Was unable to get command prompt last night.  After clean re-install I decided to update Ubu just in case that was the issue with no command promt.  To do so I must go to bois and disable "auto" on the VC section.  Ubu will load if I do this, if it is left on auto and connected to on board graphics then I get signal out but unreadable display.

Updated Ubu, restarted with bios set to auto and new VC connected.  Still unable to get to command at blank screen.  Alt+Clt+F1 will not work.  

The only way I can get term or a command prompt is by disabling auto for VC in bios and running off of onboard graphics.  So, it seems if I do this then running the reconfigure is a wasted effort since its not connected to the new VC.

Thoughts on getting a command prompt?

Will be later this today before I come back to this.

Thanks
Paul

---

### Post by Rocket2DMn on 2008-02-22
Can you please post the contents of your xorg file as well as this other command:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

### Post by Ecclesia on 2008-02-22
About your new build... I have a card which I'm assuming is similar, an evga 530/7150.  I know there's are gigabyte boards using the same chipsets, so I'm thinking yours might be in the same "family".  I had some issues with with the graphics.  It would hang when trying to start X unless I booted to safe graphics mode.  It would detect resolution fine, but I had to install the 169 beta drivers from Nvidia to get 3d graphics.  I also had to install linux-backports to get sound (which doesn't really work 100% right).  Figured you might want a heads up in case the cards have the same issues.

Speaking of which, anyone know if there is a problem upgrading the video card on a board with integrated video?  I was thinking of throwing an 8600 in here so that I wouldn't have to use the beta drivers and would get better performance.  Although, I can't complain too much about the performance of the 7150.  Compiz works great and I haven't tried a ton of games (or new games) but Quake 3 is flawless at max resolution and UT2004 works smoothly as well (although has issues with textures - apparently this is due to the beta drivers).  I'm not really a gamer though, just wanted to get an idea about how well the graphics card performed.

---

### Post by Biciclettapc on 2008-02-22
> **Rocket2DMn said:**
> Can you please post the contents of your xorg file as well as this other command:
```
cat /etc/X11/xorg.coonf
lspci | grep VGA
```

Sorry about my newness but which of the 232 xorg files do you need?

---

### Post by Biciclettapc on 2008-02-22
> **Rocket2DMn said:**
> Can you please post the contents of your xorg file as well as this other command:
```
cat /etc/X11/xorg.coonf
lspci | grep VGA
```

joseph@joseph-desktop:~$ catcat /etc/X11/xorg.coonf
bash: catcat: command not found
joseph@joseph-desktop:~$ lspci | grep VGA
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
01:0b.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)
joseph@joseph-desktop:~$

---

### Post by Rocket2DMn on 2008-02-22
Sorry, I mispelled, I have fixed my post, but here it is again:
```
cat /etc/X11/xorg.conf
```
Just copy and paste that into the terminal.  You said "catcat" and i said "xorg.coonf", lol.
We can see by the second command that both cards are detected.  Get me the xorg.conf and we'll proceed.

---

### Post by Biciclettapc on 2008-02-23
joseph@joseph-desktop:~$ cat /etc/X11/xorg.conf
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Driver          "intel"
        BusID           "PCI:0:1:0"
EndSection

Section "Monitor"
        Identifier      "LCM-22w3"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Monitor         "LCM-22w3"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1680" "1680x1050" "1440x1440" "1280x1280" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection
joseph@joseph-desktop:~$

---

### Post by Biciclettapc on 2008-02-23
[B]Contents of xorg.conf file.
[/B]


 bare-bones XFree86 config to start the server in probe-only mode
Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	RgbPath		"/etc/X11/rgb.txt"
EndSection
Section "ServerFlags"
	Option "AllowMouseOpenFail"
EndSection
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"extmod"
	Load	"freetype"
	Load	"int10"
	Load	"record"
	Load	"vbe"
EndSection
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"keyboard"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection
Section "InputDevice"
	Identifier	"Generic Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
EndSection
Section "Device"
	Identifier	"Generic Device"
	Driver		"::DRIVER::"
EndSection
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Device"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		15

---

### Post by Rocket2DMn on 2008-02-23
OK from your first xorg.conf file, we have
```

Section "Device"
Identifier "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
Driver "intel"
BusID "PCI:0:1:0"
EndSection

Section "Monitor"
Identifier "LCM-22w3"
Option "DPMS"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
Monitor "LCM-22w3"
DefaultDepth 24
SubSection "Display"
Modes "1680x1680" "1680x1050" "1440x1440" "1280x1280" "1280x1024" "1280x960" "1280x800" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```

What we need is to have the nvidia card showing.  When you run dpkg-reconfigure xserver-xorg does it give you the option to select the nvidia card?
Does your card get listed under System->Administration->Screen and Graphics, Graphics Card tab?

---

### Post by Biciclettapc on 2008-02-23
Success!

Not sure why, but I imagine you guys might understand, but it now works!

I changed the default under screen and graphics to the new VC, which now appeared.  Restarted, changed bios to auto and connected the new VC and it came up!

Enabled advance desktop graphics and things look way better!

**Thank You!**  Both my son and I were about to give up on using this VC.

now if I could only find pc100 ram this Dell likes he will be in business.

:):):)

---

