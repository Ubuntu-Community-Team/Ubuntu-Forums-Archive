---
title: "Title Bar too small"
date: 2007-11-01
forum: General Help
---

### Post by marco202 on 2007-11-01
I'm using Ubuntu 7.10. The problem is, when I log in, all windows that I open have  a small font in their title bar. When X server is restarted (Ctrl - Alt - Backspace) everything comes to normal.This doesn't happens every time I login. Theme I'm using is Ubuntu's default i.e. Human. 
Thanks in advance.

---

### Post by MadMike77 on 2007-11-01
I'm having the same Problem, Ubuntu 7.10 upgraded from 7.04. On a ATI Graphics-card running with fglrx driver and Compiz.

I've found out that opening a terminal and running:
compiz --replace &
will bring the title bar fonts to the normal size for the current session. The trouble is, they will be small the next time you boot your machine :-/ 

Does anyone know anything more about this problem?

---

### Post by marco202 on 2007-11-01
Didn't know about that command. I'll try it and see if it works. Thanks!

---

### Post by marco202 on 2007-11-18
Sill after that command no change. But I just tried compiz --version and voila title bars came to normal. What can this be?

---

### Post by PmDematagoda on 2007-11-18
Enter this in a terminal:-

```
sudo gedit /usr/share/themes/Human/metacity-1/metacity-theme-1.xml

```

The scroll down to this part
```
<frame_geometry name="normal" rounded_top_left="true" rounded_top_right="true" rounded_bottom_left="true" rounded_bottom_right="true">
  <distance name="left_width" value="5"/>
  <distance name="right_width" value="5"/>
  <distance name="bottom_height" value="5"/>
  <distance name="left_titlebar_edge" value="4"/>
  <distance name="right_titlebar_edge" value="4"/>
  <aspect_ratio name="button" value="0.9"/>
  <distance name="title_vertical_pad" value="4"/>
  <border name="title_border" left="2" right="2" top="1" bottom="2"/>
  <border name="button_border" left="0" right="0" top="0" bottom="0"/>
</frame_geometry>
```

Then change the numbers of both "top=1" and "bottom=2" in this:-
```
  <border name="title_border" left="2" right="2" top="1" bottom="2"/>
```
to a bigger one such as 3, then save the file and then open up the Desktop Background Changer by right-clicking on the Desktop, the title bar should change in size after doing this.

---

### Post by marco202 on 2007-11-18
Well I can change title bar font through GUI, but sometimes it returns to the small font. Do you think that this change won't make worse in case when font size is OK at login?

---

### Post by marco202 on 2007-11-20
It didn't help. compiz --version worked again.

---

### Post by Trespasser on 2007-11-20
Put compiz --version into Startup in Sessions. It worked for me to fix the Gnome Windows Title Bar font problem.

Later.

---

### Post by marco202 on 2007-11-21
Added it. Will see if it works.

---

### Post by marco202 on 2007-11-22
So far so good.

---

### Post by tripham on 2007-12-03
I have a same problem in Ubuntu 7.10. I tried to use you all solutions without any progress so far. The windows title fonts turns very small after I booting or restarting Ubuntu, but it changes to normal size every time I re-login. Can everybody help me getting rid of this matter?

---

### Post by Coollie on 2007-12-14
> **Trespasser said:**
> Put compiz --version into Startup in Sessions. It worked for me to fix the Gnome Windows Title Bar font problem.

Later.

I Have the same problem en read all your sugestions, my question is where can I put this command, as I'm an absolute beginner I don't know where to look.

Thnx

:guitar:

---

### Post by Ninefold on 2007-12-14
I have the exact same problem.

I have compiz installed. Going to desktop effects and clicking advanced settings to "none" and then click back to compiz settings changes the title bars to the correct size. Logging out and back in, like others have said, also corrects it. I'd like to not have to do this though.

> $ compiz--version
bash: compiz--version: command not found


This command was said by others to work but I get nothing in return.

Thanks to anyone that can help.

---

### Post by lel on 2007-12-14
It's "compiz --version". There's a space between the z and the dash

---

### Post by Ninefold on 2007-12-15
Ahh... Thank you lel.

I need bigger fonts I guess. :)  Much appreciated.

---

### Post by memps001 on 2008-02-24
Gah!  I had the small title bars too, so I tried compiz - version, and got this error message:

```
/usr/bin/compiz.real (core) - Warn: Unknown option '-version'
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

The problem was fixed for the moment.  But terminal wasn't really finished, it was kind of stuck after that error message, so I closed it and now* I have no title bars at all!* Help!

---

### Post by boombox1387 on 2008-02-28
> I had the small title bars too, so I tried compiz - version

If you typed in "compiz - version", the problem may just be with the way you typed it.  Try "compiz --version" (one space, two dashes, and of course no quotes), and see if that works.

---

### Post by memps001 on 2008-02-28
I'll give that a shot, though I was able to get the command to work by running it via a Launcher from my Desktop rather than in Terminal.  It fixes the problem, of course the next time I log in, the text is small again.  So I figure "Oh, I'll just put it in my startup apps, and it'll fix it before it even happens."  No such luck.  Ends up I've just got to run the command every time I use my computer,once everything is loaded up.

---

### Post by attercop on 2008-03-08
compiz --version is setup as a startup item for me and i am still getting the tiny bar and text issue. Typing compiz --version still fixes the issue but who wants to do that everytime it happens?

---

### Post by tomtrauberts on 2008-03-20
I thought I'd bump this thread, because I'm having the same problem.

Running ```
compiz --version
``` from the session, or even from an app like "Gnome-Do" doesn't do anything for me.  I have to run it specifically from the terminal, and then it fixes the problem.

Does anyone know the cause of this issue?  Might it have anything to do with the selected monitor?

---

### Post by fillintheblanks on 2008-04-04
same problem over here.. sometimes the font is normal size other times its really small

---

### Post by KryoFrk on 2008-05-20
I too am having this problem, small text in the login screen and intermittent small window title/text. 

I have 7.10 with Nvidia FX5200 restricted drivers, and a slightly customized Human theme. I am also using 32" widescreen 720p at 1360x768 via DVI to HDMI as my main screen, and I'm wondering if that may or may not have anything to do with it? Anyone else using an HDTV as a monitor? 

My xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

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

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "JT178QP"
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "SYN 232-S12"
    HorizSync       15.0 - 58.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce FX 5200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "JT178QP"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1360x768 +0+0; DFP: nvidia-auto-select +0+0"
EndSection

```

The JT178QP is my 17" LCD I don't use unless I have issues with the system. I tried adding the -br -audit 0 -dpms -dpi 96 after  Option  "NoLogo" "True" but that just put a CLI on my 17" for 10 seconds then it went out, and nothing came up on the 32"

My xserverrc (Which I tried changing it from 100 dpi to the 75 it is now, and nothing happened);
```

#!/bin/sh
exec /usr/bin/X11/X -dpi 75 -nolisten tcp

```

My xinitrc:
```

#!/bin/sh
# $Xorg: xinitrc.cpp,v 1.3 2000/08/17 19:54:30 cpqbld Exp $

# /etc/X11/xinit/xinitrc
#
# global xinitrc file, used by all X sessions started by xinit (startx)

# invoke global X session script
. /etc/X11/Xsession

```

and I'm not sure what else would be helpful, but please ask if you feel like you can help. Thanks!

---

### Post by KryoFrk on 2008-05-21
Bumping due to timing of post being "off-peak"

---

### Post by KryoFrk on 2008-05-22
```
compiz --version
``` worked but I'm not looking for a half-fix I would like to also fix the login screen small text as well. Is there a way to run a script before the login screen?

---

