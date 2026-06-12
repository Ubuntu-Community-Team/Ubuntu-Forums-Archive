---
title: "Problem starting up (x server)"
date: 2007-02-20
forum: General Help
---

### Post by Quibly on 2007-02-20
Ok first Ill describe the problem and then Ill say why I think it happens.

Ok I start up the computer it goes normally: it says the grub loading, then kernel starting and all that. Then it says "loading essential drivers" and "mounting root file system" and it also says on the right "ok". On the toop I see the ubuntu logo.
Untill now everything is normal. But than after all thoes OKs, instead of going into the graphical login screen with the orangy background it shows a blue screen that shows the following-
> Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

Than I press NO and this is what I see-
> The X server is now disabled. Restart GDM when it is configured correctly

I press ok and than I get a completly black screen with my username and it asks me to login. I put my user and pass and then I get to the command promp (not graphical at all- only black and white).

What do I do?

By the way this is how I think I got to this problem-
I was going around the forums and then I saw a link to download a program (probably this x server thing). When installing it it asked me for a sh*tload of values. I had not clue what they were so I just entered random values. I think that this is what f**ked up the system. How do I go back to the configuration that I had before I messed it up?

By the way every time I start the system the same thing happens....


Thats it. 

By the way I have 256mb ram with pent III comp. I dont have any other OS's other than ubuntu on that comp.


Thanks a lot!!
:)

---

### Post by renzokuken on 2007-02-20
what grafix card/chipset do you have?

to reconfigure the xserver, from the black screen, login and run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Quibly on 2007-02-20
I have a very very old ATI grapics card. I bought it in 1999 or 2000. Its something like 3D Rage IIC. I want to reconfigure the x server thing so that it is back to what it was before... How do I do that?

Thanks

---

### Post by tommcd on 2007-02-20
Just boot your PC as usual. When you get to "failed X server" message press ctrl+alt+F1 simultaneously. This will give you a terminal. Login. Then do <sudo /etc/init.d/gdm stop> in terminal. This stops the X server. Then do <sudo dpkg-reconfigure xserver-xorg>. This will reconfigure the X server (the program that enables the GUI). Just accept the default values for all the questions if you don't know the answers.
Then do <sudo reboot> to reboot to the GUI.

---

### Post by web-keeper on 2007-02-26
Ok, to all users who have Compaq's with onboard ATI video cards, and maybe to those with the other ATI cards..!

I am posting this in the hope it will help those with these types of server and cards.  I personally have a Compaq 6400 and after trying both Ubuntu & Centos on it, I found myself with the error's like the following..., after trying to setup GNOME &/or KDE. 

[I][COLOR="Blue"]Build Date: 11 January 2007
Build Host:

        Before reporting problems, check [http://wiki.X.Org](http://wiki.X.Org)
        to make sure that you have the latest version.
Module Loader present
OS Kernel: Linux version 2.6.9-34.0.2.ELsmp (buildcentos@v20z-i386) (gcc version 3.4.5 20051201 (Red Hat 3.4.5-2)) #1 SMP Fri Jul 7 19:52:49 CDT 2006
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Mon Feb 26 17:31:08 2007
(EE) Unable to locate/open config file
xf86AutoConfig: Primary PCI is 0:14:0
Running "/usr/X11R6/bin/getconfig -X 60802000 -I /etc/X11,/usr/X11R6/etc/X11,/usr/X11R6/lib/modules,/usr/X11R6/lib/X11/getconfig -v 0x1002 -d 0x4756 -r 0x7a -s 0x1002 -b 0x4756 -c 0x0300"
getconfig.pl: Version 1.0.
getconfig.pl: Xorg Version: 6.8.2.0.
getconfig.pl: 23 built-in rules.
getconfig.pl: rules file '/usr/X11R6/lib/X11/getconfig/xorg.cfg' has version 1.0.
getconfig.pl: 1 rule added from file '/usr/X11R6/lib/X11/getconfig/xorg.cfg'.
getconfig.pl: Evaluated 24 rules with 0 errors.
getconfig.pl: Weight of result is 500.
New driver is "ati"
(==) Using default built-in configuration (53 lines)
(EE) open /dev/fb0: No such file or directory
(WW) ATI(0): Failed to set up write-combining range (0xf6000000,0x200000)
(WW) ATI(0): Failed to set up write-combining range (0xf6000000,0x200000)
(EE) <default pointer>: Cannot find which device to use.
(EE) xf86OpenSerial: No Device specified.
(EE) <default pointer>: cannot open input device
(EE) PreInit failed for input device "<default pointer>"
No core pointer

Fatal server error:
failed to initialize core devices

Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining[/COLOR][/I]


So after googling for endless night's and trying different things, I worked out that what I needed to do was the following and it fixed my problem.

After installing, GNOME/KDE, the X Windows System & VNCServer, I could not get it to work.  

So I did the following; -------------------

1. run the Xorg configuration program for your distro, (sorry I can't tell you as I currently have CentOS loaded).

2. Then after it created the xorg.conf file for me, I had to create a copy of the xorg.conf file from the root user directory to the /etc/X11 directory.

3. Then I had to modify the file to reflect the following ...

Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "screen0" 0 0
	InputDevice    "mouse0" "CorePointer"
	InputDevice    "keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	RgbPath      "/usr/X11R6/lib/X11/rgb"
	ModulePath   "/usr/X11R6/lib/modules"
	FontPath     "/usr/X11R6/lib/X11/fonts/misc/"
	FontPath     "/usr/X11R6/lib/X11/fonts/TTF/"
	FontPath     "/usr/X11R6/lib/X11/fonts/Type1/"
	FontPath     "/usr/X11R6/lib/X11/fonts/CID/"
	FontPath     "/usr/X11R6/lib/X11/fonts/75dpi/"
	FontPath     "/usr/X11R6/lib/X11/fonts/100dpi/"
EndSection

Section "Module"
	Load  "extmod"
	Load  "dri"
	Load  "dbe"
	Load  "glx"
	Load  "xtrap"
	Load  "vnc"
	Load  "record"
	Load  "type1"
	Load  "freetype"
EndSection

Section "InputDevice"
	Identifier  "keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	[COLOR="#2e8b57"]Option	    "Device" "/dev/mouse0"[/COLOR]
EndSection

Section "Monitor"
	Identifier   "monitor0"
	VendorName   "Nonitor Vendor"
	ModelName    "A150-X2"  
[COLOR="#2e8b57"]	HorizSync    28-63  
    	VertRefresh  55-78[/COLOR]
 
[COLOR="#2e8b57"]# V-freq: 60.00 Hz  // h-freq: 47.80 KHz
	Modeline "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796 [/COLOR]
 	
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "accel"              	# [<bool>]
        #Option     "crt_display"        	# [<bool>]
        #Option     "composite_sync"     	# [<bool>]
        #Option     "hw_cursor"          	# [<bool>]
        #Option     "linear"             	# [<bool>]
        #Option     "mmio_cache"         	# [<bool>]
        #Option     "test_mmio_cache"    	# [<bool>]
        #Option     "panel_display"      	# [<bool>]
        #Option     "probe_clocks"       	# [<bool>]
        #Option     "reference_clock"    	# <freq>
        #Option     "shadow_fb"          	# [<bool>]
        #Option     "sw_cursor"          	# [<bool>]
	Identifier  "Card0"
	Driver      "ati"
	VendorName  "ATI"
	BoardName   "3D Rage IIC 215IIC [Mach64 GT IIC]"
	ChipSet     "ati"
	ChipId      0x4756
	ChipRev     0x7a
	BusID       "PCI:0:14:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection              
[COLOR="Red"]            SubSection "Display"    
		Viewport   0 0   
		Depth     24  
	EndSubSection[/COLOR]  
EndSection
------------------------------------------------------------------------------------------

Pay carefull attention to the green highlights, these are the changes I added, and the red are the ones I deleted.

Once you have done this you can run startx, and it should start you desktop of choice.  If all has gone well you can then continue to configure VNC, and your life should become  happy again...

While there might be other better ways of fixing this issue, this was the fastest and easiest for me that worked.



Goodluck to all.
Jon (web-keeper)

---

### Post by pedrotuga on 2007-02-27
Where did you get your screen specs?

---

### Post by aberry5555 on 2007-02-27
try the following 

```
sudo dpkg-reconfigure xserver-xorg
```

When it asks you what type of gfx card you have choose "vesa" (i.e unknown or basic gfx card). Do any other settings and save, then reboot. Hopefully you will have a proper GUI on start-up. 

Now, for those of you with ATI cards (9--- and X---- series) go and open up a terminal and type in the following command:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down till you find a heading called "device" and under that should be a sub-heading called "driver". To the right of the driver should be the word "vesa" in inverted commas, change this to "radeon" then save and do ctrl+alt+backspace. This should bring you back to opensource drivers.

---

