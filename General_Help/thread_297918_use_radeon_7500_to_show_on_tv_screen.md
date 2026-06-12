---
title: "use radeon 7500 to show on tv screen"
date: 2006-11-11
forum: General Help
---

### Post by Fittersman on 2006-11-11
how can i get my ati radeon 7500 to output to a tv?

when booting it shows the ubuntu with the bar that slowly fills (loading bar) on the tv but then after that it gets out of resolution or something.

i have tried all the resolutions in system-->preferences-->screen resolution but none of them give a clear picture

---

### Post by Fittersman on 2006-11-12
anyone can help me :D

---

### Post by Fittersman on 2006-11-13
someone has to know how to get my radeon 7500 card to show properly on a tv screen!

---

### Post by ReaderRat on 2006-11-13
Shot in the dark...might help...
[**Radeon Driver Info**](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by CatKiller on 2006-11-13
This might be even more apropos:

[Radeon7500TVOut]("https://wiki.ubuntu.com/Radeon7500TVOut")

---

### Post by honda on 2006-11-14
I used this howto to get it working on ati radeon 7500
[http://www.ubuntuforums.org/showthread.php?t=215763&highlight=ati+radeon+tv+out+how+to](http://www.ubuntuforums.org/showthread.php?t=215763&highlight=ati+radeon+tv+out+how+to)
It only works when the resolution is set to 800x600 refresh rate 60Hz.

---

### Post by honda on 2006-11-14
... with dapper, I might add. Have edgy installed now but I haven't tried tvout with it yet...

---

### Post by Fittersman on 2006-11-14
well i tried all the guides but none worked unless there is something i am missing.

when i try to use the mplayer thing, mplayer just gives me an error

---

### Post by honda on 2006-12-06
Still no luck with tv-out? I had it working on dapper by the guide I posted above. Now I tried the same with edgy, post #22 in that thread contains some additions needed on edgy. It worked right away!

---

### Post by Fittersman on 2006-12-06
can you tell me how to add that extra post in there? i dont know when to use it (like what comes right before it and what comes right after)

---

### Post by honda on 2006-12-07
**From the original howto**
sudo apt-get install build-essential
sudo apt-get install xserver-xorg-dev
sudo apt-get install x11proto-xinerama-dev
sudo apt-get install x11proto-xf86misc-dev
sudo apt-get install x11proto-gl-dev
sudo apt-get install mesa-common-dev

**From post #22**
I had to download more packages:
sudo apt-get install x11proto-xf86dri-dev libdrm-dev x11proto-xext-dev x11proto-xextproto-dev x11proto-video-dev render-dev x11proto-randr-dev x11proto-fonts-dev x11proto-core-dev

*On my system apt-get could not find the package x11proto-xextproto-dev, so I just omitted it (removed from the line above), worked anyway*

**Original**
Fetch Driver and Patch:
You may want to create a directory in which to store the temporary files we'll be using.

Code:

cd ~
mkdir atidrivers
cd atidrivers

**Post #22**
I had to download different version of the driver + patch:
wget [http://megahurts.dk/rune/stuff/xorg7.1-6.6.3-tv_output.patch.gz](http://megahurts.dk/rune/stuff/xorg7.1-6.6.3-tv_output.patch.gz)
wget [http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.3.tar.bz2](http://xorg.freedesktop.org/releases/individual/driver/xf86-video-ati-6.6.3.tar.bz2)

**original**
cd xf86-video-ati-6.6.3.
export XORG_PREFIX="/usr"
export XORGCONFIG="--prefix=$XORGPREFIX --sysconfdir=/etc --localstatedir=/var"
./configure $XORG_CONFIG --with-xorg-module-dir=/usr/lib/xorg/modules
make

Back-up Current X.org Driver

STUB: The user should probably backup their current X.org driver. How is this done?
*I didn't do that...*

sudo make install

*Then I added this line to the device section of the xorg.conf file*
    Option		"TVOutput" "PAL"
*according to the "Tweaking the X.Org Configurations" section in the original how-to, rebooted the computer and set screen resolution to 800x600 using the system/adminiatration/screen resolution tool. If you don't have the 800x600 option, you have to add it, see "Tweaking the X.Org Configurations". Good luck!*

---

### Post by Fittersman on 2006-12-07
its very close but the resolution isnt good yet...

---

### Post by Fittersman on 2006-12-07
i just tried all the different options instead of "PAL" that were listed in the original thread and none of them work for me, do you have any other ideas?

---

### Post by honda on 2006-12-08
I just checked your other thread about this [http://ubuntuforums.org/showthread.php?t=302643](http://ubuntuforums.org/showthread.php?t=302643)
Your xorg.conf seems to have an intel chipset in the device section??

Section "Device"[B]
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset [/B]Integrated Graphics Device"
        Driver          "ati"
        BusID           "PCI:1:9:0"
EndSection

That can't be right... Mine says ati radeon 7500 something on that row... Possibly you have both integrated intel graphics and radeon, but the radeon is obviously working anyway.. really don't know how to proceed, sorry.

---

### Post by Fittersman on 2006-12-08
yeah the radeon one is the one im using it just that i had been changing that intel part to the radeon one so much i just thought that since it doesnt matter i wont bother anymore :D but yeah the computer is using the radeon one. thanks for all your help though

---

### Post by markofealing on 2006-12-28
Dell Latitude C640
Kubuntu Edgy 6.10
ATI Radeon Mobility M7 LW [Radeon Mobility 7500]

Followed the post and got to the end without any real problems except I can not get the laptop screen to display in 800x600, I just get horizontal lines and corruption of the image. The TV output is the same and when I switch to my Hitachi multi sync monitor it fails to handle the resolution.

I can get a "clean" image in 640x480 and 1024x768, both at 60Hz. I'm using the Dell 1024x768 Laptop Display Panel driver, but I've also tried it with the Plug and Play driver with the same result. I suspect it may be the display type I've chosen has the wrong vertical and horizontal settings but I'm not sure what they should be 

I think if I can crack this issue I will have it working!! :) 

BTW: A neat tip if you are unable to read your PC screen due to corruption of the display and have a 2nd PC, is to ensure you are running TightVNC or similar on your problem PC and then connect via VNC into your problem PC from the 2nd PC.

You can then see what is on the screen and revert back to previous "working settings".

Below is a copy if my xorg.conf file, had tried to attached but it failed :( so had to paste:

[FONT="Courier New"]# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
  FontPath "/usr/share/X11/fonts/misc"
  FontPath "/usr/share/X11/fonts/cyrillic"
  FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
  FontPath "/usr/share/X11/fonts/Type1"
  FontPath "/usr/share/X11/fonts/100dpi"
  FontPath "/usr/share/X11/fonts/75dpi"
  FontPath "/usr/share/fonts/X11/misc"
  # path to defoma fonts
  FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
  Load "i2c"
  Load "bitmap"
  Load "ddc"
  Load "extmod"
  Load "freetype"
  Load "int10"
  Load "type1"
  Load "vbe"
  load "glx"
  load "GLcore"
  load "v4l"
EndSection

Section "InputDevice"
  Identifier "Generic Keyboard"
  Driver "kbd"
  option "CoreKeyboard"
  option "XkbRules" "xorg"
  option "XkbModel" "pc105"
  option "XkbLayout" "gb"
  option "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "stylus"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "stylus"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "eraser"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "eraser"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "InputDevice"
  Driver "wacom"
  Identifier "cursor"
  option "Device" "/dev/wacom"# Change to 
  option "Type" "cursor"
  option "ForceDevice" "ISDV4"# Tablet PC ONLY
  # /dev/input/event
  # for USB
EndSection

Section "Device"
  identifier "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 0
  option "MergedFB" "off"
  option "TVOutput" "PAL"
EndSection

Section "Monitor"
  identifier "Generic Monitor"
  vendorname "Dell"
  modelname "Dell 1024x768 Laptop Display Panel"
  HorizSync 31.5-48.5
  VertRefresh 59.0-75.0
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  gamma 1.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    modes "1024x768@60" "800x600@60" "800x600@75" "800x600@72" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "ServerLayout"
  Identifier "Default Layout"
  screen 0 "Default Screen" 0 0
  InputDevice "Generic Keyboard"
  InputDevice "Configured Mouse"
  InputDevice "stylus" "SendCoreEvents"
  InputDevice "cursor" "SendCoreEvents"
  InputDevice "eraser" "SendCoreEvents"
  InputDevice "Synaptics Touchpad"
EndSection

Section "DRI"
  Mode 0666
EndSection
Section "device" # 
  identifier "device1"
  boardname "ati"
  busid "PCI:1:0:0"
  driver "ati"
  screen 1
  option "MergedFB" "off"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSectio[/FONT]n

---

### Post by Fittersman on 2006-12-28
do you know what all that DRI stuff at the end means? at the bottom of my xorg.conf file all i have is this under it:

```
Section "DRI"
        Mode    0666
EndSection

```

---

### Post by markofealing on 2006-12-30
I've just looked it up at [http://www.xfree86.org/current/DRI6.html](http://www.xfree86.org/current/DRI6.html) which contains the XFree86 DRI user guide

According to this site, the DRI section of the file is used to restrict use of direct rendering. 

The DRI entry in my xorg.conf file allows all users to access direct rendering. I hasten to add that this is not something I've entered and is present in all copies of the file on the laptop.

I've just checked my other system which is a Dell Optiplex GX1 running Ubuntu 6.10 with a Matrox G200 PCI card (rather than on board Intel graphics) and this has the same entry at the bottom of every variant of the xorg.conf file. 

Where as the laptop started with Kubuntu 6.10, the desktop started with Ubuntu 6.06.

---

### Post by markofealing on 2006-12-30
I've just added the following lines in the xorg.conf under Section monitor to specify the Horizontal and vertical frequency ranges:

    HorizSync   31.5 - 59.0
    VertRefresh 40 - 72

However, this has made no difference, I still can't get a resolution of 800x600 without severe screen corruption.:(

---

