---
title: "nVidia 6150/430 on-board video"
date: 2006-11-25
forum: General Help
---

### Post by Scottla on 2006-11-25
Hi.  Newb again.  Thanks for any assistance you can provide.

I just built a new (and first!) Ubuntu machine using the ASUS A8N-VM CSM motherboard.  This board has the nVidia 6150 and 430 chips on it which, among other things, provide onboard video.

I know the video is not as good as an independent GPU, however I have read that it is quite adequate for general use, up to and including video playback and light gaming.

In my case, the video is quite choppy.  Even when I surf, page scrolling is very "blocky" -- in other words, as I move down the page is gets to the bottom and "whites out" then moves to the next section in one big "block".  This should not be the case.

Can anyone provide me with some advice on how to tweak the video performance.  Do I need to install special drivers for that chip set, for example?  I know what I'm doing in WinXP, but Ubuntu is a whole new world to me.

Thanks for any help you can provide!

---

### Post by halfvolle melk on 2006-11-25
Hi,
Try installing the nVidia driver from the repositories:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

For the CLI it would be something like this:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```

---

### Post by Scottla on 2006-11-25
I've followed the instructions as posted in the link, however when I conduct the "sudo" command line, I get the following:

Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel.

Clearly, I installed the wrong thing.

---

### Post by Scottla on 2006-11-25
OK.  Rebooted.  Re-ran the sudo command and got:

nvidia-glx is already the newest version.
nvidia-kernel-common is already the newest version.

I assume this means that the drivers in place are the latest.  So, I hope it's not the that this is the best video performance I can get out of this board with Linux.  If so, it is significantly below what it can do in WinXP.

Any other suggestions?  Trying to surf with the pages constantly and slowly repainting in blocks is very annoying.

---

### Post by halfvolle melk on 2006-11-25
Run this
```
glxinfo|grep direct
```
The output should look like this
```
$ glxinfo|grep direct
direct rendering: Yes
```
If not
```
sudo yourfavoriteeditor /etc/X11/xorg.conf
```
and find the Device section. If the driver is "nv" change it to "nvidia". eg.
```
Section "Device"
    ...
    Driver         "nvidia"
    ...
```
Safe. Close all programs. CTRL+ALT+BAKSPACE.

---

### Post by Scottla on 2006-11-25
I'm learning.  Bear with me.  If I get good at this, I promise to pass it forward!

OK, Half, I Ran the first command and got:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

I then ran the sudo command (sudo yourfavoriteeditor /etc/X11/xorg.conf), was asked for my password, then got:

sudo: yourfavoriteeditor: command not found

Further advice appreciated!

---

### Post by halfvolle melk on 2006-11-26
I'm not sure what that error means, but what if you run the entire command? It should say that it either does or does not have direct rendering.

> **Scottla said:**
> sudo: yourfavoriteeditor: command not found
Im sorry if that was a bit unclear, but replace yourfavoriteeditor with an editor of your choise eg. vi, gedit, nano or whatever works best for you.

---

### Post by Scottla on 2006-11-26
OK.  When I run the first command you suggest, I get the same lines as I posted before.  When you say "run the whole command", does that mean I have to add some extensions or flags?

As to the sudo: told you I'm new!  I took that literally! :D  Anyway, put in gedit and it ran.  Problem is xorg.conf has NOTHING in it, at least not that came up in the editor.  I'm assuming there should be code there.

Is it possible I didn't load something crucial?

---

### Post by halfvolle melk on 2006-11-26
Erm ... are you sure you got the path right? For instance x11 is not the same as X11. Copy paste the following:
```
sudo gedit /etc/X11/xorg.conf
```
That should open a file with lots of stuff in it. Please post the entire file here between code tags so we can have a look.

As for the entire command
```
glxinfo | grep direct
```
- glxinfo spits out lots and lots of info
- | takes the output of glxinfo and gives it to grep
- grep will only print lines containing "direct" and throws the rest away

---

### Post by steveneddy on 2006-11-26
*EDIT*
Found solution [here]("http://www.ubuntuforums.org/showthread.php?t=302567&highlight=nvidia+direct+rendering")

The result of running 
> 
glxinfo|grep direct

is this
> 
steve@phoenix2:~$ glxinfo|grep direct
direct rendering: No

And here is what i consider to be the important parts of my /etc/X11/xorg.cong file
(because these are the areas that I need to change or anyone ever talks about changing)
BTW - I ran 
> 
lspci -X

to get the correct PCI address for my xorg.conf file - and yes - I blacklisted my onboard Intel video and I get much better system performance overall after that, but no direct rendering.

OK - here's the xorg.conf - can anyone tell me what I need to do to get direct rendering running on this machine?

> 
Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "Monitor"
    Identifier     "P110"
    Option         "DPMS"
EndSection

Section "Device"

#    Option	   "NvAGP"  "1"	
    Identifier     "nVidia GeForce FX5200"
    Driver         "nvidia"
    BusID          "PCI:1:10:0"
    Option         "RenderAccel" "true"	
    Option         "AllowGLXWithComposite" "On"
EndSection

Section "Screen"

#    Option	   "UseFBDev"		     "true"
    Identifier     "Default Screen"
    Device         "nVidia GeForce FX5200"
    Monitor        "P110"
    DefaultDepth    24
    
    
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


Any help appreciated.

Thanks - I believe that if I can get past this small hurdle that I will be able to have better than acceptable video performance from a well broken in system. Not to say that the video isn't good now, but I know it can be better. I have spent the weekend tweaking and think I am finally on the correct path.

Thank you for all help - SE

*EDIT* I need to add the fact that I'm running the nVidia Beta driver 1.0-9742 which, BTW, gives great performance and no issues so far.

---

### Post by halfvolle melk on 2006-11-26
> **steveneddy said:**
> *EDIT*
Found solution [here]("http://www.ubuntuforums.org/showthread.php?t=302567&highlight=nvidia+direct+rendering")
Yeah, but the OP uses Edgy + The latest driver* and therefore no longer requires XGL or AIGLX to run Beryl :)

*edit: Oh, he's not. I wa sconfused with another topic.

---

### Post by Scottla on 2006-11-26
OK.  Success with that sudo.  Perhaps it was the Cap X!

Here are the results:

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
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
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection

Section "Monitor"
	Identifier	"CM812"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"CM812"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


In "Section module" I see "Load glx", but clearly, in the device section, the nVidia driver has not registered.  Please let me know your thoughts on what went wrong.

---

### Post by halfvolle melk on 2006-11-26
> **Scottla said:**
> Section "Device"
	Identifier	"Generic Video Card"
	Driver		"vesa"
	BusID		"PCI:0:5:0"
EndSection
For 3D you'll need the driver to be "nvidia". But first
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

---

### Post by Scottla on 2006-11-26
Copy made.  What's next Obi-Wan? :)

---

### Post by halfvolle melk on 2006-11-26
Hehe, well, use the force I guess :)

Like suggested in post #5 change
**Driver "vesa"**
to
**Driver "nvidia"**
then safe the file, close all programs and finally press CTRL+ALT+BACKSPACE in order to log in again, all of this while keeping your fingers crossed.
If it doesn't work remember to
```
sudo cp /etc/X11/xorg.conf-backup /etc/X11/xorg.conf
```

---

### Post by Scottla on 2006-11-26
SWEET!  That did the trick.  Surfing smoothly and pumping out the video at high FPS.\\:D/ 

Half, thanks for the great technical assistance, as well as such a positive first experience here at ubuntuforums.org!  I'll be hanging out here more often and learning all I can.  Hopefully, in the future, I'll be walking newbs through their start-up problems.

---

### Post by halfvolle melk on 2006-11-26
Good to hear it works! But be warned, these forums are addictive ;)

---

### Post by paker on 2007-01-10
I followed the insturction and changed "vesa" to "nvidia" I got blue screen with DOS type message. What's my solution? Thanks.

---

