---
title: "Multi screen problem"
date: 2014-06-18
forum: General Help
---

### Post by David_Puljiz on 2014-06-18
Greetings,

I'm running ubuntu 14.04 LTS on a Lenovo thinkpad T440s with a thinkpad ultra dock. I have two BenQ 22' monitors which I would like to use instead of the laptop monitor. In theory the ulradock should be able to support to support 3 external monitors (VGA, DVI or DP1, HDMI or DP2). However the laptop detects only one external monitor and clones the display on both.

Here is the xrandr output:

> Screen 0: minimum 320 x 200, current 3600 x 1080, maximum 32767 x 32767
eDP1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 309mm x 175mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected 1680x1050+1920+30 (normal left inverted right x axis y axis) 473mm x 297mm
   1680x1050      59.9*+
   3360x1050      60.0  
   2560x1024      60.0  
   1280x1024      75.0     60.0  
   1440x900       75.0     59.9  
   1280x960       60.0  
   1280x800       59.8  
   1152x864       75.0  
   1152x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)



I doesn't mater which port I use or if I plug in both of them or just one, xrandr gives the same output.

I've updated the Intel Haswell drivers using the Intel Graphics installer for Linux, but the problem is still here.

Any help would be appriciated.

---

### Post by jcerruti on 2014-08-15
I have the exact same issue.
I have a lenovo T440s laptop and two external monitors: an LG and a Dell. I'm running Ubuntu 14.04 LTS.
When I connect the external monitor directly to the laptop, via mini display port and VGA, I can see them all in the Displays configuration and create a three monitor set-up.
But when I connect the laptop to the ultra dock and then the monitors via DVI and HDMI, Ubuntu recognizes the external monitors as only one and clones the output in both the external monitors.

Any suggestion on how to get both monitors individually recognized? Here is my xrandr output:

> Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 32767 x 32767eDP1 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 309mm x 175mm
   1920x1080      60.0*+   59.9  
   1680x1050      60.0     59.9  
   1600x1024      60.2  
   1400x1050      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   3840x1080      60.0  
   2560x1024      60.0  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI2 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)




---

### Post by jcerruti on 2014-08-15
Apparently this is because the new docks use something called MST now, which is not yet supported by the Linux video drivers.

There is a feature request to add MST support, including detailed information here: [https://www.libreoffice.org/bugzilla/show_bug.cgi?id=72795](https://www.libreoffice.org/bugzilla/show_bug.cgi?id=72795)

There is some ongoing work in developing this support apparently, and it may be possible to try an in-development patch (only for the brave). I haven't tried that myself yet.

It may be worth adding votes to the feature request.

---

