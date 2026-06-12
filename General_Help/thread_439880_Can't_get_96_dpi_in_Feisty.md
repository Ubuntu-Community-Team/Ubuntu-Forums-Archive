---
title: "Can't get 96 dpi in Feisty"
date: 2007-05-11
forum: General Help
---

### Post by trmiv on 2007-05-11
I was following a post on how to improve font rendering.  One part wants me to insert the following line into the monitor section of my xorg.conf if I run my resolution at 1024x768, which I do on my laptop, to force 96 dpi.

```
DisplaySize	270	203	# 1024x768 96dpi

```

So I did that, but when I do "xdpyinfo | grep resolution" to check the resolution, it says 89x92 DPI. This is after restarting X and I tried it again after rebooting, it's always 89x92. Why isn't the line I put in xorg.conf  working?  

This is an hp nc6220 laptop with Intel 915 express graphics.

---

### Post by yopnono on 2007-05-11
> **trmiv said:**
> I was following a post on how to improve font rendering.  One part wants me to insert the following line into the monitor section of my xorg.conf if I run my resolution at 1024x768, which I do on my laptop, to force 96 dpi.

```
DisplaySize	270	203	# 1024x768 96dpi

```

So I did that, but when I do "xdpyinfo | grep resolution" to check the resolution, it says 89x92 DPI. This is after restarting X and I tried it again after rebooting, it's always 89x92. Why isn't the line I put in xorg.conf  working?  

This is an hp nc6220 laptop with Intel 915 express graphics.

Well you should not need this but.. Install 915resolution and try, and make sure you are using the i810 driver.

---

### Post by trmiv on 2007-05-11
915resolution didn't work.  It's still 89x92

---

### Post by fragos on 2007-05-11
In some cases a video driver will ignore an xorg.conf option if it isn't programed for it.  One good example is trying to use settings like 1440x900 with the vesa driver.  Vesa selects the highest resolution it supports and ignores the 1440x900.  In my case this was solved with the nvidia-glx package which provides an Nvidia written 3D driver.

---

### Post by trmiv on 2007-05-14
I still haven't been able to get it to 96dpi.  The weird thing is, I was messing around with the PCLinuxOS Live cd yesterday, and it has the same issue on this computer,  xdpyinfo | grep resolution shows 89x92.

---

### Post by yopnono on 2007-05-14
> **trmiv said:**
> I still haven't been able to get it to 96dpi.  The weird thing is, I was messing around with the PCLinuxOS Live cd yesterday, and it has the same issue on this computer,  xdpyinfo | grep resolution shows 89x92.

Maybe the display don't support a higher value. Is the screen blurry, what is the recommended resolution?

---

### Post by Ken_Lewis81 on 2007-05-14
By my calculations, you're running at 90dpi on the diagonal of your monitor.  The GUI setting for the screen DPI is done in the Font configuration box (System -> Preferences -> Font -> Advanced), where you can set 96 DPI.

Hope that helps.
Take care.
Ken.

---

### Post by trmiv on 2007-05-14
I'm not trying to set the resolution though, my resolution is fine.  The laptop screen only supports 1024x768, and that is what I have it at.  I'm trying to set the DPI that X server is running in to 96.  The DisplaySize setting in the xorg.conf should work, but it's apparently being ignored for some reason because I can jack the two numbers all over the place and it doesn't have any effect.

---

### Post by RedSquirrel on 2007-05-14
Try this instead:

Create the file ~/.Xresources and put this line in it:

```
Xft.dpi: 96
```


Test with:

```
xrdb -query  | grep dpi
```

---

### Post by fragos on 2007-05-14
On my system System-> Preferences-> Fonts-> "Details button" provides a place to change resolution.  I'm satisfied with the 4 high level rendering choices so I haven't made any adjustments at this level.  The resolution that has been configured for me is 96dpi.  My monitor is 1440x900, 1024x768 might limit your resolution options.

---

### Post by trmiv on 2007-05-14
You can still get an X resolution of 96 DPI if you are running 1024x768, or that line DisplaySize line wouldn't work for anyone.  Why that line is being ignored is the question.

---

### Post by fragos on 2007-05-14
I know of at least one instance where a correctly formatted xorg.conf command is ignored and a working best guess is uesd.  That case is driver specific.  I don't know that is your issue but it might be.

---

### Post by trmiv on 2007-05-14
Well I managed to get something to change.  I switched to the install xserver-xorg-video-intel driver instead of the install xserver-xorg-video-i810 driver and now the resolution says 91x91, not sure why that is.

---

### Post by trmiv on 2007-05-14
If I boot into recovery mode and then use the startx command and then run that xdpyinfo | grep resolution command, it shows as 100 x 100 dpi.  Why is it different?

---

### Post by fragos on 2007-05-14
My system says it's set to 96 dpi but the xdpyinfo command says 89x87 dpi.  My image quality is good.

---

### Post by trmiv on 2007-05-14
Well I'm really bothered by the font quality in Ubuntu, that's why I'm trying to get the 96 dpi.  The guide I followed on this forum has setting your DPI to 96 dpi as the first step in getting good font quality.  I followed all the other steps, and got my fonts much better than out of the box, but they still bother me.  I want to get it to 96 DPI just to make sure I'm doing everything I can.

---

### Post by RedSquirrel on 2007-05-15
Which guide are you following? Using the .Xresources solution works well in my experience.

---

### Post by trmiv on 2007-05-15
This guide: [http://ubuntuforums.org/showthread.php?t=20976](http://ubuntuforums.org/showthread.php?t=20976)

The .Xresources doesn't work.  If I run xrdb -query  | grep dpi yes, it shows 96, but it does that anyway without that .Xresources thing.  The xdpyinfo command still shows x running at 91x91.

---

### Post by RedSquirrel on 2007-05-15
The .Xresources thing *does* work. The Xft.dpi setting is what (nearly all of) your  applications will use for fonts, regardless of what xdpyinfo reports. You're lucky because your DPI is set to 96 automatically (by GNOME, if that's what you're using). In my case (server + Fluxbox), I have to set it manually through .Xresources.

There is a [bug in Xorg]("https://bugs.freedesktop.org/show_bug.cgi?id=9758").  You should be able to get around it by adding:

```
Option "NoDDC"
```to your Device section in xorg.conf. (Then restart X.) **WARNING:** In my xorg.conf, I give the X server lots of information about my monitor, so the monitor doesn't have to identify itself (and its settings) using DDC. I would use caution in messing around with this "NoDDC" option. I tested it on my system and it worked fine, but it depends (I think) on the other settings (or their absence) in your xorg.conf.

The other option is to patch and rebuild Xorg. :popcorn:

For me, the simplest of all these options was the .Xresources route, which *you* don't even need because the DPI is already set for you. :)

---

### Post by trmiv on 2007-05-15
I tried the DisplaySize setting on my wife's laptop and it worked.  Is this xorg bug just with Intel cards?

---

### Post by kalpik on 2007-05-15
Not just Intel, i can confirm it on my Nvida FX5700 card too!

---

### Post by wilberfan on 2007-05-16
I have an nVIDIA GeFORCE 6600+ and I can only seem to get this:

>  $ xdpyinfo | grep resolution
  resolution:    85x86 dots per inch

:(

(And I had to put in a 'modeline' entry to get 1280x1024@60 for my HP f1905e LCD screen!)

---

### Post by fragos on 2007-05-17
It seems everyone that runs xdpyinfo get a value different than configured.  I get 89x87 and am configured for 96 dpi.  My display looks fine and I wonder if the output is truly meaningful or worth worrying about.  There is no guarantee that the output of xdpyinfo is a scientific objective value.

---

### Post by RedSquirrel on 2007-05-17
> **wilberfan said:**
> I have an nVIDIA GeFORCE 6600+ and I can only seem to get this:

:(

(And I had to put in a 'modeline' entry to get 1280x1024@60 for my HP f1905e LCD screen!)

> **fragos said:**
> It seems everyone that runs xdpyinfo get a value different than configured.  I get 89x87 and am configured for 96 dpi.  My display looks fine and I wonder if the output is truly meaningful or worth worrying about.  There is no guarantee that the output of xdpyinfo is a scientific objective value.

DPI can be set in more than one way. See post #9 and post #19. ;)

---

### Post by yopnono on 2007-05-17
Don't worry about it, I have it set up at 96 an running at   resolution:    122x126 dots per inch

---

### Post by fragos on 2007-05-17
> **yopnono said:**
> Don't worry about it, I have it set up at 96 an running at   resolution:    122x126 dots per inch

Absolutely.  Of the various reports of xdpyinfo, the horizontal and vertical are never equal to each other which tells me they are arrived at by interpolation of one or two hardware register values.  That value is probably scaled to 0 thru 1 in perhaps a 32 bit register.  Calculations necessary for scaling and normalizing at the assembler or C level can have poor precision depending on the CPU and arithmetic instruction set applied.  You may be expecting something that can't be delivered.  Have you wondered why Gnome reports DPI from a saved parameter?  The answer is perhaps to avoid confusion from variable results of no consequence to the end user.

---

### Post by trmiv on 2007-05-21
What's odd is I'm trying the Sabayon livecd on this same laptop right now, and out of the box xdpyinfo reports 96x96 dpi, and xrdb also reports 96 dpi.   

Here's the xorg.conf that the Sabayon livecd is using.  I notice it uses the vesa driver.

```
Section "Files"


    #FontPath	"/usr/share/fonts/local/"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath 	"/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
    Load	"type1"
    Load	"freetype"
    Load	"extmod"
    Load	"synaptics"
    Load	"vbe"
   Load        "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option 	"AllowMouseOpenFail" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier		"Synaptics1"
    Driver		"synaptics"
    Option		"SendCoreEvents"	"true"
    Option		"Device"		"/dev/psaux"
    Option		"Protocol"		"auto-dev"
    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS TouchPads
    #Option		"MaxSpeed"		"0.7"
    #Option		"MinSpeed"		"0.18"
    #Option		"AccelFactor"		"0.08"
    #Option		"TopEdge"		"120"
    #Option		"LeftEdge"		"120"
    #Option		"BottomEdge"		"830"
    #Option		"RightEdge"		"650"
    #Option		"FingerLow"		"25"
    #Option		"FingerHigh"		"30"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    
    Option	"AutoRepeat"	"500 5"
    Option      "XkbModel"	"pc105"
    Option	"XkbLayout"	"us"
    Option      "XkbRules"      "xorg"

EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom1"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom2"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom3"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"

    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"ImPS/2"
    Option "ZAxisMapping" "4 5"
     
EndSection

Section "InputDevice"
    Identifier	"Mouse2"
    Driver	"mouse"
    Option	"Protocol"	"ImPS/2"
    Option	"Device"	"/dev/input/mice"
    Option 	"ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 43 - 60
    HorizSync	28 - 80
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "i810" # do not remove vesa
    #Option "RenderAccel" "on"
    #Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier	"Screen 1"
    Device	"VESA"
    Monitor	"Generic Monitor"
    #Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth		8
        ViewPort	0 0
        Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        Modes		"1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        Modes		"1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier	"Main Layout"
    Screen 0 	"Screen 1"
    InputDevice	"Mouse1" "CorePointer"
    InputDevice	"Mouse2" "SendCoreEvents"
    InputDevice "Synaptics1" "SendCoreEvents"
    #InputDevice "wacom1" "SendCoreEvents"
    #InputDevice "wacom2" "SendCoreEvents"
    #InputDevice "wacom3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection


```

---

### Post by bcw on 2007-05-29
Hello,

I don't think you understand what the DisplaySize option means.  Try 'man xorg.conf'.

It's the PHYSICAL size if your screen in millimeters.  It has no direct relation to the RESOLUTION of the display.  None.

X uses the resolution and the DisplaySize together to calculate how many dots to use to make things on the screen turn out the correct actual size - like having 10 point type actually come out 10 points high.

If you have a classic 4:3 ratio monitor, then use the size (NOT resolution) of the display in millimeters as the hypotenuse of a 3:4:5 right triangle and figure out the X & Y numbers from that.  X = hypotenuse * 3/5 & Y = hypotenuse * 4/5.

If you have some "wide-screen" or such monitor, you have to figure out the ratio to use, 'cause it's not 4:3 for those.  You might assume the pixels are square and use the resolution (1440:900 or whatever) to work out the sides of the triangle.  1440:900 is 8:5, for instance, and you'd substitute that for the 4:3 a classic monitor uses.  That's IF the manufacturer has used square pixels that are as high as they are wide - and I don't know about all the manufacturers and what they do.

Setting DisplaySize correctly in the first place lets you avoid all sorts of silly futzing with fonts and such - they usually come out right in the first place.

Cheers,
Bret

---

### Post by trmiv on 2007-05-29
The values I'm inputting with the displaysize option are not the issue, the issue is that it doesn't matter what values I use, nothing works.   I could put DisplaySize 1234234234 2334234234 and it wouldn't make a bit of difference because it is ignored.

This is no longer an issue, however.  I've since switched to PCLinuxOS (not because of this issue, I prefer KDE and I feel it's the best KDE distro).  DisplaySize works correctly in PCLinuxOS, but PCLinuxOS uses x.org 7.1.1

---

### Post by Gary.M on 2007-05-31
> **trmiv said:**
> The values I'm inputting with the displaysize option are not the issue, the issue is that it doesn't matter what values I use, nothing works.   I could put DisplaySize 1234234234 2334234234 and it wouldn't make a bit of difference because it is ignored.

Displaysize is ignored for me too. I get 88x88 no matter what.

Looking across the forums I wonder if xorg.conf gets ignored in some way with the Nvidia restricted drivers loaded?

I set the dpi setting under the fonts control panel to match the unalterable 88 as 88dpi and noted as I did it my screen fonts changed to nice and sharp the way I was looking for them to be. So although I couldn't used DisplaySize to set 96dpi I achieved the match by changing the font control to the value noted.

Whether this approach is right or wrong I'm now happy with my fonts and the display clarity.

---

### Post by ijanos on 2007-06-27
noDDC workaround confirmed. Intel 855GM

---

### Post by rinzwind80 on 2007-07-02
The NoDDC option did the trick. I was searching for some time now for a solution.
It's simple: xdpyinfo | grep dot should display 96 dpi, if not *and* you want this font resolution you should fix it.

Ubuntu (or Linux in general) should really do something about its default looks. Take a look at Mac OS X or  Windows. Computer users spend a lot of time watching their screen, so it should look good at default values!

Supporting companies: spend some time (and/or money) in providing decent fonts. I know it's a complicated thing, but it is really important.

---

