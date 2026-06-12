---
title: "Setting up faulty monitor with XrandR or nvidia-settings in Ubuntu 13.04"
date: 2013-05-03
forum: General Help
---

### Post by Jamie_Edwards on 2013-05-03
Hi guys,

Ok, after finding out that my one monitor has a corrupt EDID and tried to fix it to no avail, I decided it would be better to try and manually change it using either xrandr or nvidia-settings.

My question is... How can I achieve that?

Here's what xrandr has to say:
```

:~$ xrandr
Screen 0: minimum 8 x 8, current 1824 x 768, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768       60.0*+   75.0     70.1  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 800x600+1024+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        60.3*+

```

Now HDMI-0 is actually able to achieve 1920x1080. How can I add this and then use it?

Any more info needed then just ask :)

---

### Post by matt_symes on 2013-05-03
Hi

This is the general idea.

Get the modeline using ```
cvt
```.

```
xrandr --newmode "1920x1080_60" <modeline from above>
```

```
xrandr --addmode VGA-0 "1920x1080_60"
```

```
xrandr --output VGA-0 --mode "1920x1080_60"
```

Kind regards

---

### Post by Jamie_Edwards on 2013-05-04
When trying to use the cvt command, the following is outputted:

```

~$ cvt


usage: cvt [-v|--verbose] [-r|--reduced] X Y [refresh]


 -v|--verbose : Warn about CVT standard adherance.
 -r|--reduced : Create a mode with reduced blanking (default: normal blanking).
            X : Desired horizontal resolution (multiple of 8, required).
            Y : Desired vertical resolution (required).
      refresh : Desired refresh rate (default: 60.0Hz).


Calculates VESA CVT (Coordinated Video Timing) modelines for use with X.

```

Any ideas?

---

### Post by matt_symes on 2013-05-04
Hi

You need to add the resolution you want to use when you call the cvt command.

```
cvt 1920 1080
```

It will return something like this
```

matthew-S206:/home/matthew % cvt 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline **"1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync**
matthew-S206:/home/matthew % 
```

It defaults to a refresh rate of 60Hz. You can change this by adding the refresh rate to the cvt command as so. This is for 75Hz. Check to see the refresh rates your monitor can handle.

```
matthew-S206:/home/matthew % cvt 1920 1080 75
# 1920x1080 74.91 Hz (CVT 2.07M9) hsync: 84.64 kHz; pclk: 220.75 MHz
Modeline **"1920x1080_75.00"  220.75  1920 2064 2264 2608  1080 1083 1088 1130 -hsync +vsync**
matthew-S206:/home/matthew % 
```

I have highlighted in bold the mode lines you need to pass to the xrandr --newmode command.

```
xrandr --newmode "1920x1080_75.00"  220.75  1920 2064 2264 2608  1080 1083 1088 1130 -hsync +vsync
```

The xrand --addmode and --output commands just require the identifier of the new mode you added and so will be along the lines of..

```
xrandr --addmode HDMI-0 "1920x1080_75.00"
```

```
xrandr --output HDMI-0 --mode "1920x1080_75.00"
```

Run the cvt command yourself just to check the values and for the refresh rate for your monitor.

If that works, we will need to make it persistent between reboots.

**EDIT:** Just noticed that your problem is with HDMI so i changed VGA-0 to HDMI-0 in the lines above. 

When i answered your first post it was around 3.30 am here :)

Kind regards

---

### Post by Jamie_Edwards on 2013-05-05
OK, quick update:

I did the cvt and newmode commands but when it came to the addmode one, the following happened:
```

~$ xrandr --addmode HDMI-0 "1920x1080_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32

```

And that in turn prevented me from going any further...

---

### Post by matt_symes on 2013-05-05
Hi

What graphics driver are you using ?

Kind regards

---

### Post by Jamie_Edwards on 2013-05-05
I'm using the nVidia x-server driver 304.88... I'm guessing that makes a bit of a difference?

---

### Post by matt_symes on 2013-05-07
Hi

> **Jamie_Edwards said:**
> I'm using the nVidia x-server driver 304.88... I'm guessing that makes a bit of a difference?

I'm wondering if this may be a bug in the driver. I'll do some research, when i get the time, for you.

Kind regards

---

### Post by Jamie_Edwards on 2013-05-07
Thank you so much, and I might have a go at re-installing 13.04 a little later on so if I do, I'll give the above commands another try and see if they work then...

---

### Post by Jamie_Edwards on 2013-05-08
Ok so here's an update:

I re-installed Ubuntu 13.04 and after logging in, I gave xrandr another bash, this was the output:
```

~$ xrandr
Screen 0: minimum 320 x 200, current 2944 x 1080, maximum 8192 x 8192
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 connected 1920x1080+1024+0 (normal left inverted right x axis y axis) 735mm x 420mm
   1920x1080      50.0*+   60.0  
   1920x1080i     30.0     25.0  
   1280x720       50.0     60.0  
   1440x576i      25.0  
   1440x480i      30.0  
   720x576        50.0  
   720x480        59.9  
   640x480        59.9  
VGA-1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 307mm x 230mm
   1024x768       60.0 +   75.1*    70.1  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  

```

Ok, I thought, I'll try putting in
```
~$ xrandr --output HDMI-1 --mode 1920x1080
```
I had to put "HDMI-1" because that's what it's known to Ubuntu now.

and it worked..! Kinda... You see, I have a new problem, which I can't fix via the TV and that's overscan, and it's quite bad too, it's preventing me from seeing the top bar in unity on my HDMI screen.

So the new question here is, how do I get rid of the overscan in xrandr? ( If it's possible of course )

P.S. Thank you for helping me get this far! It's much appreciated :)

---

### Post by Jamie_Edwards on 2013-05-09
Any idea's?

---

### Post by Jamie_Edwards on 2013-05-11
I've managed to figure out what I need, although I decided to downgrade to 12.04 as for me, 13.04 was still a little too buggy. That being said, this is what I did...

After searching other forums for a little while longer, I found some commands to which I tweaked a little:
```

~$ xrandr --output --set underscan on
~$ xrandr --output --set "underscan hborder" 38
~$ xrandr --output --set "underscan vborder" 23

```

That worked amazingly. So now I needed to make it persistant, so again I looked in some odd forums and found that using arandr might work, so I installed that and saved the file and then went into lightdm.conf file (found in "/etc/lightdm/lightdm.conf ( making a backup just in case ) ) and used:
```

# Custom desktop resolution script
session-setup-script=/usr/share/desktop-resolution-setup.sh

```

The session-setup-script path is where I saved the file I got from arandr to.

I rebooted to find that it worked, but not to the extent I wanted it to. Now I know from past experience that shell scripts use pretty much the same commands as the default terminal, only, you're able to save them and reuse them by calling that .sh file.

So I opened my desktop-resolution-setup.sh file and added:
```

xrandr --output HDMI-1 --set underscan on
xrandr --output HDMI-1 --set "underscan hborder" 38
xrandr --output HDMI-1 --set "underscan vborder" 23

```

to it, saved the file and then restarted the computer. I then logged in and to my surprise ( cause I didn't think it would work at the time) it actuallly worked, and properly.

There is a little glitch in the bottom left hand corner of the HDMI screen but I can live with that for the moment.

I might go back to 13.04 a little later on with this script and then give it another go to see if it'll work then but anyhow, thank you very much for your help :)

---

### Post by matt_symes on 2013-05-11
Hi

Not sure if i helped you much at all. The only nvidia card i have is in a GUI-less, headless server. I was hoping someone else may have chipped into the thread.

I really appreciate you posting back your results and solution. I have made a note of them for my own future reference.

Thank you :KS

I'll mark this thread as solved for you.

Kind regards

---

### Post by Jamie_Edwards on 2013-05-11
Ok, and thanks for marking it solved too.

I'll post back if it works in Ubuntu 13.04 as well for anyone that has the same problem as I did.

---

