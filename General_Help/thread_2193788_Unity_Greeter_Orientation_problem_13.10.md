---
title: "Unity Greeter Orientation problem 13.10"
date: 2013-12-14
forum: General Help
---

### Post by r_avital on 2013-12-14
in 13.04 Raring, I had the following:
/etc/lightdm/lightdm.conf: ```
display-setup-script=/etc/lightdm/lightdmxrandr.sh
```
and the entire contents of /etc/lightdm/lightdmxrandr.sh:```
#!/bin/sh
xrandr -o left
```

This worked well, giving me a greeter in portrait (vertical) orientation.

Since the upgrade to 13.10, the greeter has reverted back to landscape.  I changed: 
```
display-setup-script=/etc/lightdm/lightdmxrandr.sh
``` to: ```
greeter-setup-script=/etc/lightdm/lightdmxrandr.sh
``` ..which is supposed to execute when a greeter is started.  Same result.

Any ideas?  Again, the only change here is the upgrade from 13.04 to 13.10.

---

### Post by r_avital on 2013-12-27
bump

---

### Post by waterhead on 2013-12-29
I have a similar problem.

I have 13.10 installed on a tablet. Auto-rotation works, but it incorrectly reads the accelerator and boots rotated left! I can manually rotate it, but the method in the latest xrandr has changed.

First, determine the name of the display output:

```
xrandr -q
```

Mine is LVDS1, so to rotate it left use this:

```
xrandr --output LVDS1 --rotate left
```

You should be able to run that command in a terminal to see if it works.

Unfortunately, I can't seem to get my orientation to stick. I see it change, then change back. I think it is my accelerator doing it. I would be interested if it works for you, without an accelerator intervening.

---

### Post by r_avital on 2014-01-09
waterhead, thank you so much!

I tried your suggestion, I'm getting the same result:  My session is oriented to the left (vertical), but not the greeter.

Here's the output of xrandr-q on my end:```
Screen 0: minimum 8 x 8, current 1200 x 1600, maximum 8192 x 8192
VGA-0 connected primary 1200x1600+0+0 left (normal left inverted right x axis y axis) 432mm x 324mm
   1600x1200      60.0*+
   1400x1050      74.9     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
LVDS-0 connected (normal left inverted right x axis y axis)
   1920x1080      60.0 +
HDMI-0 disconnected (normal left inverted right x axis y axis)
```This is a laptop connected to an external monitor via KVM.  The laptop's screen resolution is in fact 1920x1080, the asterisk is on VGA-0 at 1200x1600 - am I correct to conclude that VGA-0 is the correct name xrandr uses for the external monitor?

Here's the full contents of /etc/lightdm/lightdm.conf
```
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter
display-setup-script=/etc/lightdm/lightdmxrandr.sh
```and here is the contents of lightdmxrandr.sh:```
#!/bin/sh
xrandr --output VGA-0 --rotate left
```
I don't believe I'm running an accelerator, but have no idea how to find that out.  I'll be literally ecstatic if you could show me how to verify that, and in turn be able to help you out with any info I find out.

Thanks in advance :)

---

### Post by r_avital on 2014-01-20
bump

---

### Post by waterhead on 2014-01-21
I was actually just looking at this again, and I don't have anything new to add to this. Does your screen rotate when you manually run the udated script?

The answer to this problem may be in the lightdm.conf file, but I can not find any good examples on the correct configuration of this file. You can find a version of this file here:

/usr/share/doc/lightdm/lightdm.conf.gz

That has more examples in it. I am especially interested in these entries:

```
# xserver-command = X server command to run (can also contain arguments e.g. X -special-option)
# xserver-layout = Layout to pass to X server
# xserver-config = Config file to pass to X server
```

But, without any examples of what type of command to pass, I am at a dead end. I also noticed that this example file has spaces on either side of the "=" sign. The actual file in /etc/lightdm/ does not.

As for your laptop having an accelerometer (I mistakenly called it an accelerator). Most laptops wouldn't have one, as they are usually meant to be viewed in only landscape/normal mode. But, there are some higher-grade laptops that have one that is used as a sort of "drop sensor". I believe this kicks in to lock the hard drive heads in case it senses that it has been dropped.

---

### Post by r_avital on 2014-05-24
Solved.  There was a minor hardware issue, plus some PEBCAK.

Moderators, feel free to delete thread.

---

