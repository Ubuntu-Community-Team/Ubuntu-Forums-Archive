---
title: "Interesting Thing"
date: 2007-12-23
forum: General Help
---

### Post by mariano.pelizzari on 2007-12-23
Guys,

I was trying to enable compiz fusin with xinerama with no luck until a did this (I'm using a GeForce with 2 screens)

run nvidia-setting (/usr/bin) as root
configure everything as separte screens with xinerama
apply and save
reboot
run nvidia-setting (/usr/bin) as root again
enable twin-view
apply and save
a got an xrandr error
I accept and reboot and I have twin view with xinerama and compiz fusion. Really just f... great. I'm not an expert but I know this shouldn't be working but it is.

I can post a xorg.conf if somebody wants. So far is working great.

---

### Post by ~LoKe on 2007-12-23
I don't see a problem?

Oh, and you don't have to reboot.  Just ctrl+alt+backspace.

---

### Post by mariano.pelizzari on 2007-12-23
There is not a problem. Just something that a wanted to post becouse I see many people looking for this over the forums in internet. As far as I know if you are using Twin View the bars extends over the screens and because of what I did they actually don't witch is great for me.

Thks

---

### Post by ~LoKe on 2007-12-23
> **mariano.pelizzari said:**
> There is not a problem. Just something that a wanted to post becouse I see many people looking for this over the forums in internet. As far as I know if you are using Twin View the bars extends over the screens and because of what I did they actually don't witch is great for me.

Thks

Ah.  Xinerama and TwinView aren't the same thing.

You can have two separate screens, with their own panels.  You can also have one big screen, where the panel stretches.

---

### Post by mariano.pelizzari on 2007-12-23
Yeah, I know, but you can't have both of them together, right?
That's what a did.

---

### Post by ~LoKe on 2007-12-23
> **mariano.pelizzari said:**
> Yeah, I know, but you can't have both of them together, right?
That's what a did.

No, you can't have both of them together, that's a paradox.

You can have two screens with their own taskbars, yet still be able to move windows from one screen to another.  This is how I have gnome set up.

---

### Post by mariano.pelizzari on 2007-12-23
In that way you can't use compiz fusion, can you?

---

### Post by ~LoKe on 2007-12-23
> **mariano.pelizzari said:**
> In that way you can't use compiz fusion, can you?

Sure I can.  I can have one big cube or two, one on each monitor.

---

### Post by mariano.pelizzari on 2007-12-23
Are you using nvidia's driver? because if I enable separate screens with xinerama I can't use compiz fusion, at least the way it cames preinstaled in gusty
Any tip you can give to do it.

thks

---

### Post by ~LoKe on 2007-12-23
> **mariano.pelizzari said:**
> Are you using nvidia's driver? because if I enable separate screens with xinerama I can't use compiz fusion, at least the way it cames preinstaled in gusty
Any tip you can give to do it.

thks

I use TwinView not Xinerama, I think. Here are the important lines of my xorg.conf
> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
    Load           "glx"
EndSection

Section "Monitor"
    Identifier     "DELL 1907FP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "DELL 1907FP"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "2560x1024,null; 1600x1200,1600x1200; 1280x1024,1280x1024; 1024x768,1024x768"
    Option         "UseDisplayDevice" "DFP"
    Option         "AddARGBGLXVisuals" "True"
    Option	       "AddARGBVisuals"	"True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
       Option         "Composite"   "Enable"
 EndSection

Section "DRI"
	Mode 0666
EndSection

---

### Post by mariano.pelizzari on 2007-12-23
Mine is slightly different. I'm going to mes with it and see what a get.

Thks for your help.

---

