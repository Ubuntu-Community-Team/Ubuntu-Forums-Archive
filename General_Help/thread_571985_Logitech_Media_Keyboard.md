---
title: "Logitech Media Keyboard"
date: 2007-10-09
forum: General Help
---

### Post by crache on 2007-10-09
[FIXED] Mysteriously, or maybe not so, started working. I was playing with my .xmodmap, I dunno.. seems to be working now. I must have missed something along the way, but I don't think this is something that wasn't working right to begin with. compiz still isn't recognizing my super L, but a little playing around and I should be on track. I will leave this in case it is any help to anyone. 

I am  using Kubuntu 7.10 beta 1. I have a Logitech media keyboard, specifically [this model.]("http://www.logitech.com/index.cfm/keyboards/keyboard/devices/186&cl=us,en") There is nothing out of the ordinary with this keyboard, except maybe that it doesn't have a scroll lock. My problem is the windows modifier key. Xev reports it as keycode 115 which seems pretty standard. KDE control center maps its Win key to mod4, and mod4 is listed in the X Modifier Mapping box as key Super_L. The key is not functional in kde, or compiz (where I discovered the problem). Here are the xev details:

```

KeyPress event, serial 30, synthetic NO, window 0x2800001,
    root 0x52, subw 0x0, time 2279262493, (70,-289), root:(75,497),
    state 0x0, keycode 115 (keysym 0xffeb, Super_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

```

Now, from what I can remember, things should be working fine. If not I hope someone can point the obvious out to me, as this has been quite a bit of trouble and research hasn't turned much up. Installation defaulted to pc105 for keyboard model. Audio, volume, mute buttons etc worked out of the box. I've tried a few others 102, 103, various Logitech mappings, but I don't think that is the problem. If anyone has any insight on this it would be greatly appreciated.

Thank you,
        Josh


PS. What is the deal with shift+backspace half killing the x server (everything disappears, brings me to kdm login... odd, related?
Maybe not, [https://launchpad.net/ubuntu/+source/xserver-xgl/](https://launchpad.net/ubuntu/+source/xserver-xgl/) 
    + Use xmodmap to disable shift-backspace killing Xgl
It would be nice to disable that, anyone know how to go about it?
[edit]
[http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/](http://customisinglife.wordpress.com/2006/11/13/disable-shift-backspace-restarting-xgl/) Here is a solution.
[/edit]

---

