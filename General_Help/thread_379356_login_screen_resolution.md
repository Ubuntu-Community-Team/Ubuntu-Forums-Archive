---
title: "login screen resolution"
date: 2007-03-08
forum: General Help
---

### Post by stchman on 2007-03-08
Hello all, is there a way to set the login screen resolution?  The login screen wants to do 1600x1200 and my monitor has problems with that resolution.  I run my desktop at 1280x1024 and would like the login screen to be that resolution as well.  Are there any config files that can be edited?

Thanks

---

### Post by PapaNerd on 2007-03-08
Try editing the /etc/X11/xorg.conf file and removing the higher resolution "Modes".

---

### Post by x1a4 on 2007-03-08
> **PapaNerd said:**
> Try editing the /etc/X11/xorg.conf file and removing the higher resolution "Modes".

Be sure to restart X after you're done.  

Ctrl+Alt+Backspace, or 
*sudo /etc/init.d/gdm restart*

If you have a nvidia card, install *nvidia-settings* (highly recommended) to configure your display settings.

---

### Post by stchman on 2007-03-09
> **PapaNerd said:**
> Try editing the /etc/X11/xorg.conf file and removing the higher resolution "Modes".

I fixed the problem.  If you edit your xorg.conf and make your preferred resolution appear first in the line e.g. "1280X1024" then Ubuntu will use it first.

Now if I can just get the monitor refresh thing working.

---

### Post by x1a4 on 2007-03-09
> **stchman said:**
> 

*<snip>*

Now if I can just get the monitor refresh thing working.

Open your monitor's manual and check what refresh rates it can handle.  If you don't have the manual, see you're monitor's manufacturer's website.  

Open _/etc/X11/xorg.conf_ for editing, 

In Section "Monitor" edit 
    HorizSync       24.0 - 62.0
    VertRefresh     50.0 - 75.0

The numbers above are for my own monitor, make sure to replace those with values supported by your monitor.  

To adjust your monitor's gamma set the Gamma value
ie: 

Gamma  1.0

If you monitor supports it you might also want to enable DPMS for better display quality 

Option   "DPMS"


Restart X when you've made your changes.

---

### Post by stchman on 2007-03-12
> **x1a4 said:**
> Open your monitor's manual and check what refresh rates it can handle.  If you don't have the manual, see you're monitor's manufacturer's website.  

Open _/etc/X11/xorg.conf_ for editing, 

In Section "Monitor" edit 
    HorizSync       24.0 - 62.0
    VertRefresh     50.0 - 75.0

The numbers above are for my own monitor, make sure to replace those with values supported by your monitor.  

To adjust your monitor's gamma set the Gamma value
ie: 

Gamma  1.0

If you monitor supports it you might also want to enable DPMS for better display quality 

Option   "DPMS"


Restart X when you've made your changes.

I tried that and it did not work.  As far as brightness running the nvidia-settings allowed me to adjust the brightness and gamma.

I did find a workaround, I went into the xorg.conf and removed and resolution greater then 1280x1024 and that worked, but I just cannot find a way to adjust the refresh rate.

There has to be a way.

---

### Post by x1a4 on 2007-03-12
Make sure you have the latest version of the nvidia driver installed.  The latest version of *nvida-settings* has the means to change refresh rates.  

You can also try this in your _/etc/X11/xorg.conf_

in **Section "Device"** set the **Driver** to **"nvidia"** (with quotes)

in **Section "Screen"** set **DefaultDepth** to **24** and add this option: 

**Option "metamodes" "1024x768_[color=blue]75[/color] +0+0; 1024x768 +0+0; 800x600 +0+0; 640x480 +0+0"**

replace **[color=blue]75[/color]** with the refresh rate you want.  Make sure your monitor supports that refresh rate.


[color=red]If this doesn't work, please post the contents of your _/etc/X11/xorg.conf_ file along with information about your monitor and video card.[/color]


For more information regarding _xorg.conf_ run *man 5x xorg.conf* from a terminal, or use the Ubuntu Help Center to view the xorg.conf man page.

---

### Post by jimbob on 2007-03-12
I just tried to install nvidia-settings and it wants to un-install nvidia-glx - what's up with that?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by x1a4 on 2007-03-12
> **jimbob said:**
> I just tried to install nvidia-settings and it wants to un-install nvidia-glx - what's up with that?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

Don't install Nvidia from the repositories.  Instead, download the driver from [Nvidia.com](http://www.nvidia.com/content/drivers/drivers.asp)

Logout, then go to a console by pressing Ctrl+Alt+F1, and login.  

Stop X: 

*sudo /etc/init.d/gdm stop*

Install the driver:  

*sudo sh /driver/download/location/NVIDIA-Linux-x86-1.0-9755-pkg1.run*

Start X: 

*sudo /etc/init.d/gdm start*

EDIT: The driver comes with all the Nvidia software you need, including *nvidia-settings* and even an over-clocking application called *nvclock_gtk*

---

### Post by jimbob on 2007-03-13
Thanks - but do I have to uninstall my original driver(s) before I do this or will it overlay all the old stuff?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by x1a4 on 2007-03-13
> **jimbob said:**
> Thanks - but do I have to uninstall my original driver(s) before I do this or will it overlay all the old stuff?


The Nvidia installer will do everything for you.  Just run it and things should work well.  

BTW, what's your video card?  Let me know and I'll give you some tweaks for it.

---

### Post by jimbob on 2007-03-13
Hey, thanks!  I have an Nvidia GeForce 6600 AGP card.

I'm using the DVI port to drive my main display and the analog port to drive my second monitor (both LCD) because it has no DVI.

Posting my xorg in case you want to see it.
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jimbob on 2007-03-13
oops ...

---

### Post by x1a4 on 2007-03-13
You're loading DRI together with GLX--can't have that, one or the other but not both.  

I suggest you use GLX and edit your _xorg.conf_ to include the following.  
[color=red]Always create backups when changing system files, **especially** when changing X files.[/color]

In **Section "Module"**
```

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

```

**Section "Screen"**

The following should work for both of your displays, still, it's a good idea if you read *man 5x xorg.conf* for details about each option and together with your monitor's manual verify your monitors support everything.  

To create a PostScript file of a man page, for easier reading, do the following: 
*man -t 5x xorg.conf > /documents/path/man_xorg.conf.ps*

```

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

```

**Extras:** 
```

# comment this out if you don't want compositing
Section "Extensions"
    Option         "Composite" "Enable"
EndSection

# this is for DRI, we're not using it so leave commented
# Section "DRI"
#        Mode 0666 
# EndSection

```


EDIT: 

In **Section "ServerLayout"**
```

Option         "AIGLX" "true"  # comment this out when when using DRI

```

---

