---
title: "i810 to intel - dual head in Gutsy"
date: 2007-10-22
forum: General Help
---

### Post by Macuyiko on 2007-10-22
This is my xorg.conf as it is now:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection



Section "Module"
        Load "i2c"
        Load "GLcore"
        Load "bitmap"
        Load "ddc"
        Load "dbe"
        Load "dri"
        Load "extmod"
        Load "freetype"
        Load "glx"
        Load "int10"
        Load "type1"
        Load "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

#deleted input devices for tablets

Section "Device"
        Identifier      "0 Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        Option "XAANoOffscreenPixmaps"
        #Option "DDCMode" "true"
        #Option         "VBERestore" "yes"
        #Option         "AGPMode" "4"
        Option          "MonitorLayout" "CRT,LFP"
        BusID           "PCI:0:2:0"
        Screen          0
EndSection

#devices using thinkwiki: agpmode, devicepresence, no ddcmode and crt,lfp

Section "Device"
        Identifier      "1 Intel Corporation Mobile Integrated Graphics Controller"
        Driver          "i810"
        Option "XAANoOffscreenPixmaps"
        #Option "DDCMode" "true"
        #Option         "VBERestore" "yes"
        #Option         "AGPMode" "4"
        Option          "MonitorLayout" "CRT,LFP"
        Option          "DevicePresence"        "yes"
        BusID           "PCI:0:2:0"
        Screen          1
EndSection

#LCD
Section "Monitor"
        Identifier      "Laptop Monitor"
        Option          "DPMS"
EndSection

#dock
Section "Monitor"
        Identifier      "External Monitor"
        Option          "DPMS"
        HorizSync 28-49
        VertRefresh 60-72
EndSection

Section "Screen"
        Identifier      "Main Screen"
        Device          "0 Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "Laptop Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "Second Screen"
        Device          "1 Intel Corporation Mobile Integrated Graphics Controller"
        Monitor         "External Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           8
                Modes           "1600x1200@60" "1024x768@60"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1600x1200@60" "1024x768@60"
        EndSubSection
        SubSection "Display"
                Depth           24
                #mode for samsung
                Modes           "1600x1200@60" "1024x768@60"
        EndSubSection
EndSection

Section "ServerLayout"
        #Option "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          0 "Main Screen"
        Screen          1 "Second Screen" LeftOf "Main Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Disable"
EndSection
```

As you can see, I have a second screen to the left of my main (Laptop) screen. Since Feisty I have been having random freezes and x-restarts which have become worse with Gutsy (the dreaded Error in I830WaitLpRing() problem). Since most people had success with the new 'intel' driver I wanted to try that (it is also the default driver a dpkg-reconfigure xserver-xorg gives me).

So I changed i810 to intel, but then X won't start and outputs a backtrace. So is there a way I can use this setup with Intel drivers? Or do I have to use xrandr-voodoo?

Thanks!

---

### Post by Macuyiko on 2007-10-22
Bump. In the meantime I've tried setting up a xrandr-configuration with the intel drivers, which works.

However, everytime I use my VGA output (attached screen), Gnome wants to move all my panels and icons the that monitor, which I find extremely annoying.

Is there any way to tell Gnome that my laptop screen is the main one on which the desktop should stay?

Could this have something to do with the order xrandr finds/outputs my screens?

```
Screen 0: minimum 320 x 200, current 2048 x 768, maximum 2048 x 2048
VGA connected 1024x768+0+0 (normal left inverted right) 408mm x 306mm
   1600x1200      60.0 +   59.9  
   1280x1024      75.0     59.9  
   1280x960       59.9  
   1152x864       75.0     74.8  
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
LVDS connected 1024x768+1024+0 (normal left inverted right) 246mm x 185mm
   1024x768       50.0*+   60.0     40.0  
   800x600        60.3  
   640x480        60.0     59.9 
```

---

### Post by dysphasi on 2007-10-24
From what I gather xrandr always assumes the attached monitor/tv is the primary and I can't seem to find a way to change that as such.

What you can do though is initiate a line to switch your panel etc.. back to the laptop,

```
 gconftool --type int --set /apps/panel/toplevels/top_panel_screen0/monitor 1 
```

...for example will set your main ubuntu gnome bar to the laptop. 

Don't know if it'll be any help to you but here is a [[color=red]**thread I started**[/color]](http://ubuntuforums.org/showthread.php?t=583566) to show you what I did.

I was actually a bit quick to set it as 'solved' however. The thing that bugs me still is that if I start my laptop up with the external screen (in my case a tv via svideo) it automatically configures a mirrored screen at login, my xrandr changes aren't saved. 

As such, even though I can run the script I've linked to, my icons still get shoved about in the mirrored screen -> extended screen process, due to my tv being narrower than the laptop and the bar being squashed to fit it. Annoying!

Don't spose you've any words of wisdom?

---

### Post by Macuyiko on 2007-10-29
Thanks, that helps, and I've modified your script a bit and I'm using it now.

I do have the same problem as you however: my icons get shoved to the other screen, but that's not such a big of a deal.

However I've been having another annoying problem since using intel+xrandr. Every time I close my laptop screen, the screens blank (as they should), but not always (sometimes I have to open and close it again). Then, once blanked, I hear the login sound. So Ubuntu's logging me out instead of just keeping my screen locked. I have to login again once I open my laptop. Any ideas why this is happening? Thanks.

---

### Post by dysphasi on 2007-10-29
What version of ubuntu are you using?

In 7.10 (don't have prior experience with others I'm afraid), all I have to do is go to:

System -> Preferences -> Power Management

and then select your preferences for "when laptop lid is closed". I don't know about your machine, but with any laptop I've used the screen will automatically turn off anyway when you close it (hard-wired), so there's no need to go overkill and get ubuntu to turn off the display for you.

Just change the setting to 'Do Nothing', your laptop screen will still turn off when you close it most likely, and the tv-out won't be messed up either when you do so.

Hope this is of some help.

Oh, with regards to the icon shifting, I've been experimenting with alternate options in gconf-editor (Alt+F2, type in gconf-editor).

Then go to apps->panel-> and objects and applets. From here you can set "pane_right_stick" to your buttons etc.. in the toolbar. Fingers crossed, sticking all those buttons to the right of the center line to this option has kept them behaving...so far. I'll report back after a bit more use. :)

---

### Post by Macuyiko on 2007-10-29
> **dysphasi said:**
> What version of ubuntu are you using?

In 7.10 (don't have prior experience with others I'm afraid), all I have to do is go to:

System -> Preferences -> Power Management

and then select your preferences for "when laptop lid is closed". I don't know about your machine, but with any laptop I've used the screen will automatically turn off anyway when you close it (hard-wired), so there's no need to go overkill and get ubuntu to turn off the display for you.

I know. My setting was 'blank screen'. Which I liked because then Ubuntu blanked my external screen too, and it would lock my desktop so that I had to retype my password to login again.

I've set it to 'Do Nothing' for the time being tho...

> **dysphasi said:**
> Then go to apps->panel-> and objects and applets. From here you can set "pane_right_stick" to your buttons etc.. in the toolbar. Fingers crossed, sticking all those buttons to the right of the center line to this option has kept them behaving...so far. I'll report back after a bit more use. :)

Good tip! This might help some people (I'm just dragging my panels over, it's not much of a hassle).

---

### Post by dysphasi on 2007-10-29
Hmmm, not come across the blank screen problem like that,

...but then again I only use my laptop to work on here and hook it up to a tv to watch media center/mythtv.

The buttons are a little more stable, but still jiggle about at times. It doesn't seem to be consistent.

Goodnes only knows why gnome panel can't stick to a specific screen rather than just screen 0, 1 etc... it should be TV or LVDS etc.. then again randr should really allow a --primary option. They're all to blame!!

---

