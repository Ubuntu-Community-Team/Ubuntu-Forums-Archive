---
title: "resolution differs..."
date: 2007-10-28
forum: General Help
---

### Post by jayaramk on 2007-10-28
when i first installed the ubuntu gutsy 7.10 i had a resolution of 800X600 so i changed it into 1024X768 stilll when i start my compuiter at the login screen i get the resolution of 800X600 and inside after the login 1024X768 ?? how can i solve this in order to make the resolution of the login screen as that of the normal

---

### Post by Gaunt on 2007-10-28
Yeah I have the same problem but my Kubuntu 7.10 Gutsy boots up and loads with a much higher resolution than the 1024*768 that i want. Also some times the resolution does not set to the specified 1024*768 when I log in. I have also had a lot of problems with graphics and crashes that has forced me to reinstall so I have to say: Bulletproof X? My foot! Sometimes when I have booted up in failsafe low graphics It will not allow me to configure the driver I want. There isa a general trouble that some applications dont start when I start them and so on. Im sorry to say that the monkey is monkeying around a little too much. Hopefully this gets fixed soon.

---

### Post by jayaramk on 2007-10-28
buzzzzzzzzzzzzzzzzzz.... any solution????

---

### Post by Thanawho on 2007-10-28
Having the same problem here...We need to find a definitive solution to this. Running a hp dv6500 laptop with nVidia geforce 8 series w/ a 15" widescreen monitor. This is not a *huge* problem, but it would make my Ubuntu 7.10 install flawless(which is all that matters, right :)) I've heard several different solutions to this, none of which have worked. All the solutions involved editing the "Virtual" and "Modes" portion of the xorg.conf, which did not work for me. The GDM (login screen) seems to be running at 800x600 while my desktop is running at 1200x800. Similar to the other users, this problem occured after I installed my nVidia drivers. 

Heres the section from my xorg.conf:
Section "Screen"
	Identifier	"Default Screen"
	Device		"Failsafe Device"
	Monitor		"Failsafe Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	960
		Modes		"1280x960@60"	"1280x1024@60"	"1024x768@60"	"800x600@60"	"800x600@56"	"640x480@60"
	EndSubSection

Thanks for the help. Please respond if you have had similar issues, as this seems to be a common problem.

---

### Post by Gaunt on 2007-10-29
Exactly my problem only complete oposite. GDM is in 1200x800 and when loged in its 1024x768 but sometimes it does not set the 1024x768. Very annoying

---

### Post by nowshining on 2007-10-29
if ur using a nvidia card u'll have to configure it via the nvidia-settings program if u installed the nvidia drivers from nvidia -

open up a terminal and type
sudo nvidia-settings and change it from there.

---

### Post by jayaramk on 2007-10-29
> **nowshining said:**
> if ur using a nvidia card u'll have to configure it via the nvidia-settings program if u installed the nvidia drivers from nvidia -

open up a terminal and type
sudo nvidia-settings and change it from there.


i don't have a graphic card on my system!!!!!

---

### Post by Cannaregio on 2007-10-29
Maybe slightly related.
I have the same problem, but so to say "the other way round":

[LIST]
[*]2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
[*]NVIDIA GEFORCE 6200SE
[*]Samsung Syncmaster 913v
[/LIST]

Start resolution is 1400*1050
But my xserver runs at 1280*1024 (and thus leaves space on both sides of the central screen). I *can* fix it temporarily to 1400*1050 through nvidia settings, but every time I restart I go back to 1280*1024 (or worse, see below).

Nvidia-settings
Once modified those virtual "metamodes"

```
    Option         "metamodes" "1400x1050 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
```

 (see code at the bottom of the next snippet) I cannot "save to x configuration file" through my nvidia-settings ("unable to create/delete new backup"), and EVEN IF I JUST [COLOR="#0000ff"]sudo copy[/COLOR] the following, thus created "[COLOR="#0000ff"]show preview[/COLOR]" xorg.conf in /etc/X11 and suubstitute the original xorg.conf (see the second snippet at the bottom of this post),   restarting the xserver wont work...

```
Section "Monitor"
    Identifier     "SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV44 [GeForce 6200SE TurboCache (TM)]"
    Driver         "nvidia"
    Option         "UseFBDev" "true"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200SE TurboCache(TM)"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV44 [GeForce 6200SE TurboCache (TM)]"
    Monitor        "SyncMaster"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1400x1050 +0+0; 1152x864 +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection
```

...and in fact when I restart I go back to a 800*600 resolution and have to restore the previous, non nvidia-settings modified xorg.conf in oirder to get back my 1280*1024 display.

Now a couple of points.
With Feisty 7.04 I had 1400*1050 working fine.
Compiz is enabled and works.

System --> Administration --> screens and graphics gives me as "screen 1" "model custom 1" with a screen resolution of 1280*1024. If I try to chose the right manufacturer and model (Samsung SyncMaster 913V) it asks for a driver (and afaik there are no drivers for linux).


This is my [COLOR="Blue"]actual[/COLOR] xorg.conf, note that the syncmaster screen is correctly identified.

```
cat xorg.conf.291007 
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
        Option          "XkbLayout"     "be"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ExplorerPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation NV44 [GeForce 6200SE TurboCache (TM)]"
        Driver          "nvidia"
        Busid           "PCI:1:0:0"
        Option          "UseFBDev"      "true"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        Horizsync       30-81
        Vertrefresh     56-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV44 [GeForce 6200SE TurboCache (TM)]"
        Monitor         "SyncMaster"
        Defaultdepth    24
        SubSection "Display"
                Modes           "1280x1024"     "1152x864"      "1024x768"     "800x600"        "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection

```

Finally these are the only warnings from Xorg.0.log (there are no errors):

```
cat Xorg.0.log | grep "(WW)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) NVIDIA(0): Option "UseFBDev" is not used
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used

```

I'm sure I'll find a solution, but in the mean time, if anyone as an idea of what could be made?

The fact that I CAN have 1400*1050 "per hand", but that I cannot restart it automatically drives me nut :confused:

---

### Post by nowshining on 2007-10-29
> **jayaramk said:**
> i don't have a graphic card on my system!!!!!

well then how are u using the computer than ;), and YES U DO have one either it is in a PCI or AGP slot in ur computer or it's internal meaning it's INTEGRATED into your motherboard.

As for the nvidia-settings not sticking then u can try this then open up sessions in system prefs from the start menu and creat a new startup item..

name:
nvidia-settings
command:
nvidia-settings --load-config-only

also are to MAKE SURE any of u using the NVIDIA drivers from nvidia themselves? If not then try downloading and installing the main ones from the nvidia site themselves.

when done EXIT ALL APPS

press ctrl + alt + f1

enter ur username hit enter ur password hit enter.

issues the following command

sudo /etc/init.d/gdm stop

then hit enter and when back at the command line type sudo mv /etc/X11/xorg.conf /etc/X11/oldxorg.conf and hit enter.

cd to the directory to where u download the drives - if desktop just enter
cd Desktop

run 

sudo sh ____________.run

enter ur password and follow the instructions and let it build a custom kernel. the Blank line aster sh is the name of the nvidia driver file.

then issue

sudo /etc/init.d/gdm start

if not then reboot by pressing ctrl + alt + delete on ur keyboard.

:) Also let it modify ur xorg.conf file.

If this does not work out for u and the screen blacks out press ctrl + alt + backspace and it may keep doing this but keep doing that sequence of keyboard commands until it stays.
Enter ur username and password.

Sudo /etc/init.d/gdm stop

sudo mv /etc/X11/xorg.conf /etc/X11/newbackupxorg.conf

then issue

/etc/X11/oldxorg.conf /etc/X11/xorg.conf

then issue 

sudo /etc/init.d/gdm start

if not press ctrl + alt + delete on ur keyboard and restart... if nothing works out for u and u get into trouble insert the live CD into the CD TRAY or DVD tray and reboot into into the live cd session and post from there. IF u have dialup make a backup of gnome-ppp or kppp whichever u are using onto external media first by backing up the deb file and then install it once in the live cd session and dialup from there.. :)

---

### Post by jayaramk on 2007-10-29
when i click on the restricted drivers manager it tells me that "YOUR HARDWARE DOESN'T NEED ANY RESTRICTED DRIVERS" so whats i installing the nvidia drivers and making a big process sadi above??? what after still doing such a big job if i don't get the gdm screen as 1024X768????

---

### Post by Thanawho on 2007-10-29
Its gotta be easier than that. There's some line in xconf.org that isnt being read correctly...

---

### Post by Gaunt on 2007-10-29
As said before. Never had this problem in Feisty. Andf besides that i run ATI-graphics

---

### Post by shields on 2007-10-29
I've been using Ubuntu on the same machine for over a year.  I updated my system last week to Gutsy and this problem came up just today. 

My video card shows up as:
NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]

---

### Post by utnubuk on 2007-10-29
I got this problem too and I have no separate graphics card, new install no upgrade and with no known issues in Feisty. After much "sudo dpkg-reconfigure -phigh xserver-xorg" 'ing' back and forth in the system settings, I am now at the point when my login menu is still the esoteric 1680x1050 that was already present with the live CD, but at least my desktop is at 1024x768 as it should be after loading fully. 

However, the weird resolution after start up can't be very healthy for my aging monitor, which is switching itself off in protest several times before arriving at the desktop. I got an old Highscreen MS1795P which is not listed in the list of the monitor and dispay settings of KDE.

I've tried editing the xorg config file, to no avail. Since I don't use a separate graphics card, I can't install proprietary drivers. There seem to be two different bosses at work not realizing they are commanding the same work force, instructing them to do different things.

Is this a big bug?

---

### Post by Davidh777 on 2007-10-29
Hi,
My problem is similar, I think. I tried connecting a belkin kvm switch and it messed up the resolution. I removed that but the problem persisted. Now I get to the ubuntu splash screen and just after that it goes to a static like image (color and pattern) and it shows Recommended mode 1280x1024 60Hz and a question mark in a box below it. I cannot log in, it does not get that far. I had switched to the nvidia drivers a while back without problem. I think the only way I may be able to fix this is in recovery mode, but I am not very familiar with the command line. I may need to change resolution? I was wondering if I just installed 7.10 over it if it would fix the problem. It is dual boot with windows XP so I don't want to mess up my ability to get to windows either. Thanks for any help. Oh and the monitor is a SyncMaster 914v.

---

### Post by utnubuk on 2007-10-29
In the recovery mode, the command _sudo dpkg-reconfigure -phigh xserver-xorg_ allows you to reset the display setting. It has always helped me when I messed up the Xorg.config file. This won't affect your other installations like windows, since they are on another partition. 

You can of course always run a Live CD and see how Gutsy recognizes your hardware before installing it "over". 

A system setup which has helped me greatly as an eternal newbie is a separate home partition. If I mess up things bad I just reinstall the system freshly, in the manual option of the installation I select the basic root partition to be the only one to be formatted, /home and /windows partitions are assigned as such and not formatted of course. After a quick new install all is good again. 

However, my display woes with Gutsy were there right from the start, even in the live CD which was like an omen for the things to come. I'll follow the different forum posts on this for some more days, then I'll just switch back to Feisty where I never had such problems. I may also load Feisty in the CD and compare the /etc/Xorg.config file to see how that is different.

---

### Post by shields on 2007-10-29
> **utnubuk said:**
> I may also load Feisty in the CD and compare the /etc/Xorg.config file to see how that is different.

If you do that, post here and let us know what you learn.

Thanks.

---

### Post by Thanawho on 2007-10-29
Don't you think that resetting the xconf is a little drastic? The actual desktop resolution is fine , its just the login screen. X is reading *something* that causes the login screen to change resolution and then change back after logging in. Could it be something in the nvidia-settings panel? After looking through the X configuration section, everything is set to 1200x800, which is correct. Again, the underlying problem seems to be that the login screen is either too big (low resolution: 800x600) or too small (high resolution: 1680x1050). I've read numerous posts about people editing the xconf.org, all of which have not worked.It seems as though two different "things" are conflicting with each other, causing a resolution change. Does anyone have a solution to this?

---

### Post by Davidh777 on 2007-10-29
> **utnubuk said:**
> In the recovery mode, the command _sudo dpkg-reconfigure -phigh xserver-xorg_ allows you to reset the display setting. It has always helped me when I messed up the Xorg.config file. This won't affect your other installations like windows, since they are on another partition. 

You can of course always run a Live CD and see how Gutsy recognizes your hardware before installing it "over". 

I tried it and it (sudo dpkg-reconfigure -phigh xserver-xorg)  did not change anything. I downloaded the live Gutsy CD earlier today and tried to run that to see what would happen. I got a pattern of strips with the same message, not optimum resolution 1280x1024 60Hz. I will download the Fiesty version again and try that live CD to see what happens.

Thanks.

---

### Post by isetyawan on 2007-10-30
I had a similar problem. My desktop is 1024x768 but my login screen is 800x600. Here's what I did to solve the problem. I simply add the following option in the "Monitor" Section of the xorg.conf:

```
Option "PreferredMode"  "1024x768" 
```

Reboot, and voila! my login screen is 1024x768, 

Hope this helps... and don't forget to backup xorg.conf first!

Cheers,

- Iwan

---

### Post by jayaramk on 2007-10-30
> **isetyawan said:**
> I had a similar problem. My desktop is 1024x768 but my login screen is 800x600. Here's what I did to solve the problem. I simply add the following option in the "Monitor" Section of the xorg.conf:

```
Option "PreferredMode"  "1024x768" 
```

Reboot, and voila! my login screen is 1024x768, 

Hope this helps... and don't forget to backup xorg.conf first!

Cheers,

- Iwan

thanks man its working!!!!

---

### Post by shields on 2007-10-30
> **utnubuk said:**
> In the recovery mode, the command _sudo dpkg-reconfigure -phigh xserver-xorg_ allows you to reset the display setting. It has always helped me when I messed up the Xorg.config file..

This worked for me.  I didn't do it in recovery mode.  I did it in the terminal.  Doing this resets the system display to the default settings.  I wonder what else it reset?  :)

Thanks for all the help!

---

### Post by isetyawan on 2007-10-30
Hi jayaramk,

Glad to hear that the workaround works. I hope that a better solution will soon be available. 

Cheers,
- Iwan

---

### Post by nowshining on 2007-10-30
wow isetyawan i'll remember that :)

---

### Post by isetyawan on 2007-10-31
If enough people is afflicted by this problem, perhaps we should add this workaround to a FAQ or sticky thread?

---

### Post by techflat on 2007-10-31
> **isetyawan said:**
> I had a similar problem. My desktop is 1024x768 but my login screen is 800x600. Here's what I did to solve the problem. I simply add the following option in the "Monitor" Section of the xorg.conf:

```
Option "PreferredMode"  "1024x768" 
```

Reboot, and voila! my login screen is 1024x768, 

Hope this helps... and don't forget to backup xorg.conf first!

Cheers,

- Iwan

Thanks isetyawan, your solution worked for me.

Cheers

---

### Post by utnubuk on 2007-10-31
Interestingly, the _Option "PreferredMode"  "1024x768"_ did nothing for me or reasons unkown..., my log in menu is still 1680x1050. 

To the person who was asking whether editing the Xorg.config file is a bit drastic when you got a working desktop, I don't think so. Especially if you got a "loud" monitor like mine. Highscreens are known for the loud "clackclack" sound every time they switch resolution or wake up from a screensaver. Right now, when I boot the monitor switches "on and off" (with the loud clack sound every time) so many times before the desktop stands. This is not only very annoying (and avoidable with correct permanent settings/configuration), but I also don't think that this is very good for it. Wrong resolutions are known to damage hardware, and my monitor actually does turn off when arriving at the log in menu, I have to wiggle the mouse to wake it up. So this is definitely a situation  that I will change by either finding a working solution or going back to Feisty.

I'm now torrenting Feisty again, which I couldn't find on CD, to compare the Xorg.config file and I will just post both of them once I'm done.

Otherwise I'm perfectly happy with Gutsy, even my stoneage TV-card was recognized and I now can hook up my analog VCR or watch TV with more functions available as I have in XP with the restrictive Pinnacle software.

---

### Post by isetyawan on 2007-10-31
Hi utnubuk,

Too bad the workaround doesn't work for you. Just checking: is "1024x768" listed as an available mode? (Look at the "Device" section in the xorg.conf file). Or, it is possible that the driver your're using doesn't support "PreferredMode" option. In the xorg.conf's manual, it is mentioned that only certain drivers support this option.

---

### Post by utnubuk on 2007-11-02
Hi Isetyawan,

I'm not using a separate graphics card, just what was on the board. Here is my Gutsy Xorg.config, I'm not sure what do add on the device section.

(BTW, my comparison Feisty Xorg.config from the Live CD isn't available yet, it didn't copy unto the USB device, and I don't have write permission to my harddrive. I'll have to email it to myself...)

[HTML]# xorg.conf (xorg X Window System server configuration file)
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
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
	Driver		"sis"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-160
	Option		"PreferredMode"  "1024x768"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection[/HTML]

---

### Post by utnubuk on 2007-11-02
Ok, here's my Feisty Xorg.config for comparison. The log in menu there is the correct resolution. It may look a little weird because I had to save it as a text file and email it to myself. The camera, which I'm using as a USB storage didn't want as I had wanted.

[HTML]# /etc/X11/xorg.conf (xorg X Window System server
configuration file)
#
# This file was generated by dexconf, the Debian X
Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the
xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg
package upgrades *only*
# if it has not been modified since the last upgrade
of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be
automatically updated
# again, run the following command:
# * sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
********FontPath********"/usr/share/fonts/X11/misc"
********FontPath********"/usr/share/fonts/X11/cyrillic"
********FontPath********"/usr/share/fonts/X11/100dpi/:unscaled"
********FontPath********"/usr/share/fonts/X11/75dpi/:unscaled"
********FontPath********"/usr/share/fonts/X11/Type1"
********FontPath********"/usr/share/fonts/X11/100dpi"
********FontPath********"/usr/share/fonts/X11/75dpi"
********# path to defoma fonts
********FontPath
"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
********Load****"i2c"
********Load****"bitmap"
********Load****"ddc"
********Load****"dri"
********Load****"extmod"
********Load****"freetype"
********Load****"glx"
********Load****"int10"
********Load****"vbe"
EndSection

Section "InputDevice"
********Identifier******"Generic Keyboard"
********Driver**********"kbd"
********Option**********"CoreKeyboard"
********Option**********"XkbRules"******"xorg"
********Option**********"XkbModel"******"pc105"
********Option**********"XkbLayout"*****"us"
EndSection

Section "InputDevice"
********Identifier******"Configured Mouse"
********Driver**********"mouse"
********Option**********"CorePointer"
********Option**********"Device"****************"/dev/input/mice"
********Option**********"Protocol"**************"ImPS/2"
********Option**********"ZAxisMapping"**********"4 5"
********Option**********"Emulate3Buttons"*******"true"
EndSection

Section "InputDevice"
********Driver**********"wacom"
********Identifier******"stylus"
********Option**********"Device"********"/dev/input/wacom"
********Option**********"Type"**********"stylus"
********Option**********"ForceDevice"***"ISDV4"*********# Tablet PC ONLY
EndSection

Section "InputDevice"
********Driver**********"wacom"
********Identifier******"eraser"
********Option**********"Device"********"/dev/input/wacom"
********Option**********"Type"**********"eraser"
********Option**********"ForceDevice"***"ISDV4"*********# Tablet PC ONLY
EndSection

Section "InputDevice"
********Driver**********"wacom"
********Identifier******"cursor"
********Option**********"Device"********"/dev/input/wacom"
********Option**********"Type"**********"cursor"
********Option**********"ForceDevice"***"ISDV4"*********# Tablet PC ONLY
EndSection

Section "Device"
********Identifier******"Silicon Integrated Systems [SiS]
65x/M650/740 PCI/AGP VGA Display Adapter"
********Driver**********"sis"
********BusID***********"PCI:1:0:0"
EndSection

Section "Monitor"
********Identifier******"Generic Monitor"
********Option**********"DPMS"
********HorizSync*******28-51
********VertRefresh*****43-60
EndSection

Section "Screen"
********Identifier******"Default Screen"
********Device**********"Silicon Integrated Systems [SiS]
65x/M650/740 PCI/AGP VGA Display Adapter"
********Monitor*********"Generic Monitor"
********DefaultDepth****24
********SubSection "Display"
****************Depth***********1
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
********SubSection "Display"
****************Depth***********4
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
********SubSection "Display"
****************Depth***********8
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
********SubSection "Display"
****************Depth***********15
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
********SubSection "Display"
****************Depth***********16
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
********SubSection "Display"
****************Depth***********24
****************Modes***********"1024x768" "800x600" "640x480"
********EndSubSection
EndSection

Section "ServerLayout"
********Identifier******"Default Layout"
********Screen**********"Default Screen"
********InputDevice*****"Generic Keyboard"
********InputDevice*****"Configured Mouse"
********InputDevice * * "stylus"********"SendCoreEvents"
********InputDevice * * "cursor"********"SendCoreEvents"
********InputDevice * * "eraser"********"SendCoreEvents"
EndSection

Section "DRI"
********Mode****0666
EndSection[/HTML]

---

### Post by isetyawan on 2007-11-02
Hi utnubuk,

First, I have to correct my earlier post. The available modes are listed under the "Screen" section, not under "Device". My apologies for any confusion.

Now, in my xorg.conf, there is an entry under the "Screen" section there is an entry that looks like this:
```

Section "Screen"
     ...
     SubSection "Display"
            Modes   "1152x864" "1024x768" "800x600" "640x480"
     EndSubSection
EndSection

```

AFAIK, this entry shows the resolution that my monitor (and graphics card) can display. I don't see this entry in your xorg.conf. That may explain why "PreferredMode" doesn't work for you.
The solution,  I think, is to add this section yourself. There is probably a risk of damaging your monitor if you put unsupported mode, though (I'm not sure, can anyone confirm?). Or at least you may get a blank screen (X doesn't start at all). In this case, you'd have to login to a console (eg., Ctrl-Alt-F1) to repair your xorg.conf.

Hope this helps...

Cheers, 
- Iwan

---

### Post by utnubuk on 2007-11-02
***Yes*** that worked:-) 

I just removed that first resolution as I know that my monitor doesn't support it. The monitor still switches off and on when going from the login menu to loading the desktop, but now the login menu is at either 800x600 or 1024x768, not sure which of both. But that doesn't matter, at least it's now at a resolution I know my monitor supports. Thanks a lot.

I also learned [in this tutorial]("http://ubuntuforums.org/showthread.php?t=258484") that the Xorg.config set resolutions kick in relatively late. At other stages in the bootup values may be passed on from the BIOS.

---

### Post by utnubuk on 2007-11-02
I've also gathered the correct refresh rates for my monitor from the web and changed those as well. Wow, everything is so crisp now. And I always thought that the monitor is aging, it's from 1996 and has survived things, no monitor has probably ever had to endure, including a fire!

Anyway, just for anyone who might be interested in such things, I post the first log of Xorg I get when I use the Gutsy Live CD on my system (which remember, doesn't start with the correct screen resolution at all).


[HTML]X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux ubuntu 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686
Build Date: 29 September 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  2 12:09:32 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
	Entry deleted from font path.
(==) FontPath set to:
	/usr/share/fonts/X11/misc,
	/usr/share/fonts/X11/100dpi/:unscaled,
	/usr/share/fonts/X11/75dpi/:unscaled,
	/usr/share/fonts/X11/Type1,
	/usr/share/fonts/X11/100dpi,
	/usr/share/fonts/X11/75dpi,
	/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81ea440
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0650 card 0000,0000 rev 80 class 06,00,00 hdr 80
(II) PCI: 00:01:0: chip 1039,0001 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0962 card 0000,0000 rev 25 class 06,01,00 hdr 80
(II) PCI: 00:02:1: chip 1039,0016 card 0000,0000 rev 00 class 0c,05,00 hdr 00
(II) PCI: 00:02:5: chip 1039,5513 card 1849,5513 rev 00 class 01,01,80 hdr 00
(II) PCI: 00:02:7: chip 1039,7012 card 1849,7012 rev a0 class 04,01,00 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1849,7001 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1849,7002 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0900 card 1849,0900 rev 90 class 02,00,00 hdr 00
(II) PCI: 00:09:0: chip 1397,2bd0 card 1397,2bd0 rev 02 class 02,80,00 hdr 00
(II) PCI: 00:0a:0: chip 109e,036e card bd11,1200 rev 11 class 04,00,00 hdr 80
(II) PCI: 00:0a:1: chip 109e,0878 card bd11,1200 rev 11 class 04,80,00 hdr 80
(II) PCI: 01:00:0: chip 1039,6325 card 1849,6325 rev 00 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,2), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x0000a000 - 0x0000afff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xdfd00000 - 0xdfefffff (0x200000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xcfa00000 - 0xdfbfffff (0x10200000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI: (0:10:0) Brooktree Corporation Bt878 Video Capture rev 17, Mem @ 0xdfcfe000/12
(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 65x/M650/740 PCI/AGP VGA Display Adapter rev 0, Mem @ 0xd0000000/27, 0xdfee0000/17, I/O @ 0xac00/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xe0000000 from 0xe3ffffff to 0xdfffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[2] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[3] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[4] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[5] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[10] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[1] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[2] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[3] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[4] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[5] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[6] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[7] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[8] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[9] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[10] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[11] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[12] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[13] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[14] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[15] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[16] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[8] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[9] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
	compiled for 1.3.0, module version = 2.1.0
	Module class: X.Org Font Renderer
	ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.13.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "sis"
(II) Loading /usr/lib/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 0.9.1
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.2
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.1
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS660/[M]661[F|M]X/[M]670/[M]741[GX]/[M]760[GX]/[M]761[GX]/[M]770[GX],
	SIS340
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40)
(II) Primary Device is: PCI 01:00:0
(--) Chipset SIS650/M650/651/740 found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[8] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[9] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[17] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[18] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[19] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[20] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[21] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[22] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[5] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[6] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[7] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[8] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[9] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[10] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[11] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[12] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[13] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[17] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[18] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[19] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[20] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[21] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[22] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[23] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[24] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[25] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
	[26] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[27] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) SIS(0): SiS driver (2005/09/20-1, compiled for X.org 1.3.0.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See http://www.winischhofer.at/linuxsisvga.shtml
(II) SIS(0): *** for documentation and updates.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0xAC00
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(II) SIS(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "1.11.19" found (old SiS data layout)
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Using HW cursor
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(II) SIS(0): WARNING: Using the Hotkey might freeze your machine, regardless
(II) SIS(0):          whether enabled or disabled. This is no driver bug.
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		http://www.winischhofer.at/linuxsispart1.shtml#sisctrl
(==) SIS(0): DRI disabled
(II) SIS(0): Checking OS for SSE support is not supported in this version of X.org
(II) SIS(0): If your OS supports SSE, set the option "UseSSE" to "on".
(--) SIS(0): DIMM0 is DDR SDRAM
(--) SIS(0): DIMM1 is DDR SDRAM
(--) SIS(0): DIMM2 is not installed
(--) SIS(0): DIMM3 is not installed
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 332.892 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xD0000000
(--) SIS(0): MMIO registers at 0xDFEE0000 (size 64K)
(--) SIS(0): VideoRAM: 65536 KB
(II) SIS(0): Using 64960K of framebuffer memory at offset 0K
(--) SIS(0): SiS650 revision ID 90 (M650 A1 AA)
(--) SIS(0): Hardware supports two video overlays
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): Gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction is disabled
(--) SIS(0): Memory bandwidth at 32 bpp is 665.784 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(--) SIS(0): CRT1 DDC probing failed
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 65472 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6325
(II) SIS(0): VESA VBE OEM Product Rev: 1.11.19
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(II) SIS(0): VESA VBE DDC read successfully
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 340 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Using real widescreen modes for CRT1 VGA devices
(II) SIS(0): 	Use option "ForceCRT1VGAAspect" to overrule
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Generic Monitor: Using hsync range of 30.00-70.00 kHz
(II) SIS(0): Generic Monitor: Using vrefresh range of 50.00-160.00 Hz
(WW) SIS(0): Unable to estimate virtual size
(II) SIS(0): Clock range:  10.00 to 340.00 MHz
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1600x1200" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (hsync out of range)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (hsync out of range)
(II) SIS(0): Not using default mode "2048x1536" (hsync out of range)
(II) SIS(0): Not using default mode "2048x1536" (hsync out of range)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x720" (hsync out of range)
(II) SIS(0): Not using default mode "1280x960" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x768" (hsync out of range)
(II) SIS(0): Not using default mode "1400x1050" (hsync out of range)
(II) SIS(0): Not using default mode "1152x864" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(II) SIS(0): Not using default mode "1280x854" (hsync out of range)
(--) SIS(0): Virtual size is 1680x1050 (pitch 1680)
(**) SIS(0): *Default mode "1680x1050": 147.1 MHz, 65.2 kHz, 60.0 Hz
(II) SIS(0): Modeline "1680x1050"  147.08  1680 1784 1968 2256  1050 1051 1054 1087 +hsync +vsync
(**) SIS(0): *Default mode "1400x1050": 122.9 MHz, 65.4 kHz, 60.1 Hz
(II) SIS(0): Modeline "1400x1050"  122.90  1400 1488 1640 1880  1050 1051 1054 1087 +hsync +vsync
(**) SIS(0): *Default mode "1280x1024": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x1024"  107.86  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync
(**) SIS(0): *Default mode "1280x1024": 78.7 MHz, 46.4 kHz, 86.8 Hz (I)
(II) SIS(0): Modeline "1280x1024"   78.75  1280 1400 1520 1696  1024 1026 1032 1069 interlace +hsync +vsync
(**) SIS(0): *Default mode "1280x960": 107.9 MHz, 59.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x960"  107.86  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync
(**) SIS(0): *Default mode "1280x854": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x854"  107.86  1280 1328 1440 1688  854 958 962 1066 +hsync +vsync
(**) SIS(0): *Default mode "1360x768": 87.7 MHz, 48.5 kHz, 60.0 Hz
(II) SIS(0): Modeline "1360x768"   87.70  1360 1416 1696 1808  768 770 782 808 +hsync +vsync
(**) SIS(0): *Default mode "1280x800": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x800"  107.86  1280 1328 1440 1688  800 931 935 1066 +hsync +vsync
(**) SIS(0): *Default mode "1152x864": 107.9 MHz, 67.4 kHz, 74.9 Hz
(II) SIS(0): Modeline "1152x864"  107.86  1152 1216 1344 1600  864 865 868 900 +hsync +vsync
(**) SIS(0): *Default mode "1152x864": 89.9 MHz, 53.5 kHz, 60.0 Hz
(II) SIS(0): Modeline "1152x864"   89.89  1152 1216 1472 1680  864 869 877 892 +hsync +vsync
(**) SIS(0): *Default mode "1280x768": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x768"  107.86  1280 1328 1440 1688  768 915 919 1066 +hsync +vsync
(**) SIS(0): *Default mode "1280x720": 107.9 MHz, 63.9 kHz, 59.9 Hz
(II) SIS(0): Modeline "1280x720"  107.86  1280 1328 1440 1688  720 891 895 1066 +hsync +vsync
(**) SIS(0): *Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(II) SIS(0): Modeline "1024x768"   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync
(**) SIS(0): *Default mode "1024x768": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x768"   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync
(**) SIS(0): *Default mode "1024x768": 75.2 MHz, 56.6 kHz, 70.2 Hz
(II) SIS(0): Modeline "1024x768"   75.17  1024 1048 1184 1328  768 771 777 806 -hsync -vsync
(**) SIS(0): *Default mode "1024x768": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x768"   65.15  1024 1048 1184 1344  768 771 777 806 -hsync -vsync
(**) SIS(0): *Default mode "1024x768": 44.9 MHz, 35.5 kHz, 86.8 Hz (I)
(II) SIS(0): Modeline "1024x768"   44.86  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync
(**) SIS(0): *Default mode "1024x576": 94.5 MHz, 69.9 kHz, 86.5 Hz
(II) SIS(0): Modeline "1024x576"   94.50  1024 1072 1168 1352  576 690 694 808 +hsync +vsync
(**) SIS(0): *Default mode "1024x576": 78.7 MHz, 60.0 kHz, 75.0 Hz
(II) SIS(0): Modeline "1024x576"   78.75  1024 1040 1136 1312  576 686 690 800 +hsync +vsync
(**) SIS(0): *Default mode "1024x576": 65.1 MHz, 48.5 kHz, 60.1 Hz
(II) SIS(0): Modeline "1024x576"   65.15  1024 1048 1184 1344  576 688 694 806 +hsync +vsync
(**) SIS(0): *Default mode "960x600": 41.5 MHz, 37.1 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x600"   41.50  960 1008 1088 1120  600 603 609 618 +hsync +vsync
(**) SIS(0): *Default mode "960x540": 37.3 MHz, 33.8 kHz, 60.0 Hz
(II) SIS(0): Modeline "960x540"   37.29  960 976 1008 1104  540 543 549 563 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 68.2 MHz, 63.6 kHz, 100.0 Hz
(II) SIS(0): Modeline "800x600"   68.18  800 848 936 1072  600 601 604 636 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 56.2 MHz, 53.7 kHz, 85.1 Hz
(II) SIS(0): Modeline "800x600"   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(II) SIS(0): Modeline "800x600"   49.52  800 816 896 1056  600 601 604 625 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 50.1 MHz, 48.2 kHz, 72.4 Hz
(II) SIS(0): Modeline "800x600"   50.11  800 856 976 1040  600 637 643 666 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(II) SIS(0): Modeline "800x600"   39.97  800 840 968 1056  600 601 605 628 +hsync +vsync
(**) SIS(0): *Default mode "800x600": 36.1 MHz, 35.2 kHz, 56.3 Hz
(II) SIS(0): Modeline "800x600"   36.06  800 824 896 1024  600 601 603 625 +hsync +vsync
(**) SIS(0): *Default mode "768x576": 35.0 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "768x576"   35.00  768 792 872 976  576 578 581 597 +hsync +vsync
(**) SIS(0): *Default mode "720x576": 32.7 MHz, 35.9 kHz, 60.1 Hz
(II) SIS(0): Modeline "720x576"   32.73  720 744 816 912  576 578 581 597 +hsync +vsync
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 31.7 kHz, 59.8 Hz
(II) SIS(0): Modeline "856x480"   33.94  856 872 1000 1072  480 492 495 529 -hsync -vsync
(**) SIS(0): *Default mode "856x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SIS(0): Modeline "856x480"   33.94  856 904 1048 1112  480 672 680 797 interlace +hsync +vsync
(**) SIS(0): *Default mode "848x480": 33.7 MHz, 31.0 kHz, 60.0 Hz
(II) SIS(0): Modeline "848x480"   33.75  848 864 976 1088  480 486 494 517 -hsync -vsync
(**) SIS(0): *Default mode "848x480": 33.9 MHz, 30.5 kHz, 76.5 Hz (I)
(II) SIS(0): Modeline "848x480"   33.94  848 904 1048 1112  480 672 680 797 interlace +hsync +vsync
(**) SIS(0): *Default mode "800x480": 56.2 MHz, 53.7 kHz, 85.2 Hz
(II) SIS(0): Modeline "800x480"   56.25  800 832 896 1048  480 554 557 630 +hsync +vsync
(**) SIS(0): *Default mode "800x480": 49.5 MHz, 46.9 kHz, 75.1 Hz
(II) SIS(0): Modeline "800x480"   49.52  800 816 896 1056  480 551 554 624 +hsync +vsync
(**) SIS(0): *Default mode "800x480": 39.8 MHz, 37.7 kHz, 60.0 Hz
(II) SIS(0): Modeline "800x480"   39.77  800 840 968 1056  480 552 556 628 +hsync +vsync
(**) SIS(0): *Default mode "720x480": 28.3 MHz, 31.6 kHz, 61.0 Hz
(II) SIS(0): Modeline "720x480"   28.28  720 728 840 896  480 490 492 517 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 52.4 MHz, 61.7 kHz, 119.9 Hz
(II) SIS(0): Modeline "640x480"   52.35  640 680 744 848  480 481 484 515 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 43.3 MHz, 51.1 kHz, 100.3 Hz
(II) SIS(0): Modeline "640x480"   43.29  640 680 744 848  480 481 484 509 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 36.1 MHz, 43.3 kHz, 85.1 Hz
(II) SIS(0): Modeline "640x480"   36.06  640 696 752 832  480 481 484 509 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(II) SIS(0): Modeline "640x480"   31.50  640 656 720 840  480 481 484 500 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(II) SIS(0): Modeline "640x480"   31.50  640 664 704 832  480 489 491 520 -hsync -vsync
(**) SIS(0): *Default mode "640x480": 25.1 MHz, 31.3 kHz, 59.7 Hz
(II) SIS(0): Modeline "640x480"   25.06  640 656 752 800  480 490 492 525 -hsync -vsync
(**) SIS(0): *Default mode "640x400": 25.1 MHz, 31.6 kHz, 71.6 Hz
(II) SIS(0): Modeline "640x400"   25.06  640 656 752 792  400 413 415 442 -hsync +vsync
(**) SIS(0): *Default mode "512x384": 32.6 MHz, 48.5 kHz, 60.1 Hz (D)
(II) SIS(0): Modeline "512x384"   32.57  512 528 592 672  384 385 388 403 doublescan -hsync -vsync
(**) SIS(0): *Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(II) SIS(0): Modeline "400x300"   19.98  400 416 480 528  300 300 302 314 doublescan +hsync +vsync
(**) SIS(0): *Default mode "320x240": 12.5 MHz, 31.3 kHz, 60.7 Hz (D)
(II) SIS(0): Modeline "320x240"   12.53  320 328 376 400  240 245 246 258 doublescan -hsync -vsync
(**) SIS(0): *Default mode "320x200": 12.5 MHz, 31.3 kHz, 70.9 Hz (D)
(II) SIS(0): Modeline "320x200"   12.53  320 328 376 400  200 206 207 221 doublescan -hsync +vsync
(==) SIS(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) SIS(0): 2D acceleration enabled
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B]
	[1] 0	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xdfcff000 - 0xdfcfffff (0x1000) MX[B]
	[7] -1	0	0xdfff7f00 - 0xdfff7fff (0x100) MX[B]
	[8] -1	0	0xdfff8000 - 0xdfff8fff (0x1000) MX[B]
	[9] -1	0	0xdfffb000 - 0xdfffbfff (0x1000) MX[B]
	[10] -1	0	0xdfffa000 - 0xdfffafff (0x1000) MX[B]
	[11] -1	0	0xdfff9000 - 0xdfff9fff (0x1000) MX[B]
	[12] -1	0	0xe0000000 - 0xdfffffff (0x0) MX[B]O
	[13] -1	0	0xdfee0000 - 0xdfefffff (0x20000) MX[B](B)
	[14] -1	0	0xd0000000 - 0xd7ffffff (0x8000000) MX[B](B)
	[15] -1	0	0xdfcfe000 - 0xdfcfefff (0x1000) MX[B](B)
	[16] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[17] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[18] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[19] 0	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B]
	[20] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[21] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[22] -1	0	0x0000d000 - 0x0000d007 (0x8) IX[B]
	[23] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[24] -1	0	0x0000d800 - 0x0000d87f (0x80) IX[B]
	[25] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[26] -1	0	0x0000ff00 - 0x0000ff0f (0x10) IX[B]
	[27] -1	0	0x00000c00 - 0x00000c1f (0x20) IX[B]
	[28] -1	0	0x0000ac00 - 0x0000ac7f (0x80) IX[B](B)
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Reloading /usr/lib/xorg/modules//libvbe.so
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules//libint10.so
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 65472 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6325
(II) SIS(0): VESA VBE OEM Product Rev: 1.11.19
(==) SIS(0): Write-combining range (0xd0000000,0x4000000)
(II) SIS(0): Setting standard mode 0x19
(II) SIS(0): RENDER acceleration enabled
(II) SIS(0): Framebuffer from (0,0) to (1679,9896)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		32 256x256 slots
		16 512x512 slots
		32 8x8 color pattern slots
(--) SIS(0): CPU frequency 2375.79Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	432.5 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	428.4 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	59.4 MiB/s
(--) SIS(0): 	Checked MMX memcpy()... 	442.9 MiB/s
(--) SIS(0): 	Checked MMX2 memcpy()... 	475.4 MiB/s
(--) SIS(0): Using MMX2 method for aligned data transfers to video RAM
(--) SIS(0): Using MMX2 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(**) Option "dpms"
(**) SIS(0): DPMS enabled
(II) SIS(0): Using SiS300/315/330/340 series HW Xv
(II) SIS(0): Default Xv adaptor is Video Overlay
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) AIGLX: Screen 0 is not DRI capable
(II) Loading local sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) Configured Mouse: ps2EnableDataReporting: succeeded[/HTML]

---

### Post by isetyawan on 2007-11-02
Hi utnubuk,

It's nice to hear everything's going well. 

Cheers,

- Iwan

---

### Post by omrsafetyo on 2007-11-03
I was having a very similar problem to what most are having here.  Basically, I configured my xorg.conf.  This was working fine, until my widescreen (1280x768) burned out during a power surge, and I had to use an older monitor.
At that point, everytime I reboot, my video settings (in nvidia-settings gui) revert to 1280x768.  I tried to sudo into nvidia-settings - that made no difference.  I deleted the 1280x768 option from xorg.conf - same result.  

Finally, I tried something so simple, you won't even believe:  

Apply desired settings through nvidia-settings (duh, easy.  I'm thinking its going to revert again.)  However, then I go to System > Preferences > Screen Resolution ; ensure that the desired settings are there, and click Apply with  "Make these my default settings" box checked, and presto magnifico!  No more problems.  

I hope that helps someone.

---

### Post by shields on 2007-11-05
> **omrsafetyo said:**
> Finally, I tried something so simple, you won't even believe:  

Apply desired settings through nvidia-settings (duh, easy.  I'm thinking its going to revert again.)  However, then I go to System > Preferences > Screen Resolution ; ensure that the desired settings are there, and click Apply with  "Make these my default settings" box checked, and presto magnifico!  No more problems.  

I hope that helps someone.

I don't know what you mean by "Apply desired settings through nvidia-settings."

---

