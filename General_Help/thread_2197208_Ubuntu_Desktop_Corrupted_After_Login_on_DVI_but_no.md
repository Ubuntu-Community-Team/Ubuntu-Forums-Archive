---
title: "Ubuntu Desktop Corrupted After Login on DVI but not VGA"
date: 2014-01-02
forum: General Help
---

### Post by Spiralagnus on 2014-01-02
I have a dual-boot computer (Ubuntu 13.10 and Windows 7) with a VGA and a DVI-D port, an ASRock 880GM-LE FX motherboard and an integrated AMD Radeon HD 4250 graphics card. Both the VGA and DVI ports work when I log in to the Windows partition, and the VGA port works when I log into the Ubuntu partition. The DVI port works on the Ubuntu login screen, but the desktop becomes completely corrupted after I log in, as shown in the image below:

[IMG]http://i41.tinypic.com/rwmlgw.png[/IMG]

I'm not sure where the problem could be or how to begin solving it. I would appreciate any help anybody could provide. Thanks in advance!

---

### Post by tgalati4 on 2014-01-02
Look through the file /var/log/Xorg.0.log for errors.  Post any that might be helpful. Open a terminal:

```
cat /var/log/Xorg.0.log
less /var/log/Xorg.0.log
grep EE /var/log/Xorg.0.log
```

Lower the resolution of the desktop and see if both ports work.

---

### Post by Spiralagnus on 2014-01-02
Those are good suggestions, but I seem to have resolved the problem another way. I'm running a minimal install of Ubuntu with Xfce, and upgrading Xfce to 4.11/4.12 (or whatever is in the PPA right now) seems to have done it. It looks like it may have been an incompatibility problem between the earlier version of Xfce and my hardware. I'll revisit your suggestions if this current solution doesn't hold, but thank you very much for your help.

Interestingly, Ubuntu refers to this port as an HDMI port, not a DVI port:

```
me@mycomputer:~$ xrandr
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
```

Any idea why that is?

---

