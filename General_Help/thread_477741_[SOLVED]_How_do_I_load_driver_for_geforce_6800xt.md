---
title: "[SOLVED] How do I load driver for geforce 6800xt??"
date: 2007-06-18
forum: General Help
---

### Post by jawinterton on 2007-06-18
I have a XFX Geforce 6800xt and I'm having problems in ubuntu, I think because I have the wrong driver package installed.  I installed the non-legacy one.  I'm thinking I need the legacy version, but according to this:
[URL="http://http.download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt"]
http://http.download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt[/URL]
6800xt is not on the list.  

What should I do?

---

### Post by jimbob on 2007-06-18
Try installing the nvidia-glx package and the linux restricted drivers and see if that helps.  I think the package you will get will cover your hardware with no problem.

sudo apt-get install nvidia-glx
sudo apt-get install linux-restricted-drivers-$(uname -r)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

... things should be done from the command line the way Nature intended ...

---

### Post by stchman on 2007-06-18
> **jawinterton said:**
> I have a XFX Geforce 6800xt and I'm having problems in ubuntu, I think because I have the wrong driver package installed.  I installed the non-legacy one.  I'm thinking I need the legacy version, but according to this:
[URL="http://http.download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt"]
http://http.download.nvidia.com/XFree86/Linux-x86/1.0-7184/README/readme.txt[/URL]
6800xt is not on the list.  

What should I do?

In Feisty just enable tne nvidia restricted driver.

---

### Post by jawinterton on 2007-06-19
Well, the problem has gotten worse.  I heard that Envy is a nice little program to easily get your graphics card driver up and running. I tried using it following the instuctions online.   Unfortunately, now x server doesn't seem to want to load.  It tries, and then asks me if I'd like to view the X server output to diagnose the problem.  When I say yes it says:

(==) Log file: "/var/log/Xorg.0.log",
(==) Using config file: "/etc/X11/xorg.conf"
(EE) Unable to find a valid framebuffer device
(EE) NV(0): Failed to open framebuffer device, consult warnings and/or errors above for possible reasons.

and then it says just below that:
Fatal server error: no screens found

it disables the x server and tells me to restart gdm when configured correctly.  

I really don't know what to do from here guys.   I've tried to reconfigure x-org but haven't had any success.  Can I post something for ya'll to help me find out what to do?  I'm really sick of not being able to load Gnome.  

 If you want me to post my xorg.conf I don't really know how'd I'd do that seeing as I can't get Ubuntu to load it for me to post it.  I'd have to type it all out by hand on my wife's laptop here!  ](*,)   ...unless you guys have a way for me to get around that (it'd be soooo wonderful!)

BTW... I type "sudo apt-get install linux-restricted-drivers-$(uname -r)" and it tells me that it can't find that package.  (????)
I have no idea how I'd enable it if I could install it.

---

### Post by jimbob on 2007-06-20
Sorry - my bad!

It should be linux-restricted-modules-$(uname -r)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jawinterton on 2007-06-20
> **jimbob said:**
> Sorry - my bad!

It should be linux-restricted-modules-$(uname -r)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

I still cannot start gnome.  Any other suggestions?  Envy really didn't help much I guess.   It seems it really screwed up my computer.

---

### Post by jimbob on 2007-06-20
Let's have a look at your xorg.conf file.

If you have a live CD couldn't you mount the partition and make a copy of it?

For goodness sakes, don't try to type it in by hand.

I have an Nvidia geForce 6600gt which works great.  Here is my xorg.conf file.  My card has one HDMI and one vga output.  One thing that is necessary in the device section for the HDMI port to work is the line *[COLOR="RoyalBlue"]Option      "UseDisplayDevice"  "DFP"[/COLOR]*  in the Device section.  Ignore my second monitor which uses the vga port for now.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jawinterton on 2007-06-20
> **jimbob said:**
> Let's have a look at your xorg.conf file.

If you have a live CD couldn't you mount the partition and make a copy of it?

For goodness sakes, don't try to type it in by hand.

I have an Nvidia geForce 6600gt which works great.  Here is my xorg.conf file.  My card has one HDMI and one vga output.  One thing that is necessary in the device section for the HDMI port to work is the line *[COLOR="RoyalBlue"]Option      "UseDisplayDevice"  "DFP"[/COLOR]*  in the Device section.  Ignore my second monitor which uses the vga port for now.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

Do you think this will work?


Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen         "Screen0"
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
         Option         "AIGLX" "true"  # comment this out when using DRI
#        Option         "Xinerama" "on"
         Option         "Clone"    "on"
#        Option         "Twinview" "on"
EndSection

Section "Files"
	RgbPath      "/usr/share/X11/rgb"
	ModulePath   "/usr/lib/xorg/modules"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        # Load "GLCore"    # GLCore is necessary to enable OpenGL with DRI
        # Load  "dri"          # since we're using GLX comment both out
	Load  "glx"
	Load  "extmod"
	Load  "dbe"
	Load  "record"
	Load  "xtrap"
	Load  "freetype"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "int10"
        Load   "type1"
        Load   "vbe"
        Load   "v4l"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
Option	"XkbRules"	"xorg"
	Option	"XkbModel"	"pc104"
	Option	"XkbLayout"	"us"
EndSection

Section "InputDevice"
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Viewsonic"
	ModelName    "Viewsonic VA1912wb"
	HorizSync    30-82 kHz
	VertRefresh  50-85 Hz
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "Card0"
	Driver      "nvidia"
	VendorName  "nVidia Corporation"
	BoardName   "NVIDIA GeForce 6800XT"
	BusID       "PCI:1:0:0"
      Screen      0 
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        DefaultDepth    24
        Option         "AddARGBGLXVisuals" "true"
        Option         "NvAGP" "3"  # this only for display connected to a card in an AGP slot
        Option         "Accel" "true"
        Option         "RenderAccel" "true"
        Option         "AllowGLXWithComposite" "true"   # if not using compositing set to "false"
        Option         "XAANoOffscreenPixmaps" "true"
        Option         "DigitalVibrance" "0"
        Option         "Overlay" "true"
        Option         "CIOverlay" "true"
        Option         "TransparentIndex" "60"
        Option         "OverlayDefaultVisual" "false"
        Option         "SWCursor" "false"
        Option         "HWCursor" "true"
        Option         "CursorShadow" "off"
        Option         "CursorShadowAlpha" "64"
        Option         "CursorShadowXOffset" "4"
        Option         "CursorShadowYOffset" "2"
        SubSection "Display"
                Depth           24
                Modes           "1440x900" 
        EndSubSection

EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
        DefaultDepth    24
        SubSection "Display"
                Depth         24
                Modes         "1440x900"
	EndSubSection
EndSection

# comment this out if you don't want compositing
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

# this is for DRI, we're not using it so leave commented
# Section "DRI"
#        Mode 0666 
# EndSection


BTW... I'm don't have a HDMI port, and use a DVI.  Please let me know what you think.  Also,  knoppix lets me access the file but not write to it.  How do I apply these changes to my xorg.conf file?  
From there it should let me into gnome since linux-restricted-modules is installed, right?

---

### Post by jimbob on 2007-06-21
Yes, it is a DVI port - I have been doing some tv stuff lately and interchange dvi and hdmi in my confused brain.

Why do you have two "Screen0" sections in your xorg file?  Try getting rid of the second one.

Have you tried generating a new xorg.conf file from the command line after gdm fails?  This will give you a basic, no-frills xorg file to see if it works.

Type in *[COLOR="RoyalBlue"]dpkg-reconfigure -phigh xserver-xorg[/COLOR]*  Use the space bar to put a splat in front of the resolution you want.  Check to see if it put in "nvidia" for the driver and not "nv".

Then restart gdm:  [I][COLOR="RoyalBlue"]/etc/init.d/gdm restart
[/COLOR][/I]

If all else fails you might try posting your question on Alberto Milone's (Envy's author) blog here:
  [http://albertomilone.com/wordpress/?p=94](http://albertomilone.com/wordpress/?p=94)
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jawinterton on 2007-06-24
Well, I was finally able to get gnome back up and running.  I had to switch my driver in my xorg.conf file to read "vesa" instead though.  Would that forum/blog that you told me about above be the best place to figure out how to get the "nvidia" working?   Or do you have any ideas?  Thanks for your help.   I really appreciate it!:p

---

### Post by jimbob on 2007-06-24
Make sure you have universe and multiverse enabled on all uncommented lines in /etc/apt/sources.list.  If you have to add them anywhere re-run apt-get update and apt-get upgrade.

Run Synaptic, do a search on nvidia, and check to see if you have these things installed with the correct versions:

nvidia-glx  1:1.0.9631 
nvidia-kernel-common  20051028+1ubuntu
restricted-manager  0.20
xserver-xorg-video-nv   1:2.0.0-0ubuntu3
linux-restricted-modules-2.6.20.5-16.28

Look at System->preferences->Restrictred Drivers Manager and check that NVIDIA accelerated graphics driver is checked enabled and shows In use.

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jawinterton on 2007-06-26
Okay, well... I tried that and had no success.  I also tried posting various logs to albertomilone's blog.  He is sending me to nV News Forums b/c I get this error:

(WW) NVIDIA(GPU-0): Failed to determine GPU name
(II) NVIDIA(0): NVIDIA GPU Unknown (Unknown) at PCI:1:0:0 (GPU-0)

---

