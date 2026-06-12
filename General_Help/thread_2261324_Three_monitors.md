---
title: "Three monitors"
date: 2015-01-18
forum: General Help
---

### Post by Tohiko on 2015-01-18
Hello, I have a Quadro 5000 graphic adapter and I am trying to connect three monitors to it.
The adapter has 1 DVI port and 2 DisplayPort(s). However, for some reason I can only connect 2 monitors at the same time.
I am positive that my graphic adapater should be able to run 3 monitors at the same time. However, when I enable the third monitor from nvidida-config I get the message
```
MetaMode 1 of Screen 0 has more than 2 active display devices.
```

When I use xrandr I get:
```

$ xrandr  --output DP-0 --auto
xrandr: cannot find crtc for output DP-0
```

 This is my xrandr output.
```

Screen 0: minimum 8 x 8, current 3000 x 1920, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DP-0 connected (normal left inverted right x axis y axis)
   1920x1200      60.0 +
   1920x1080      60.0  
   1680x1050      60.0  
   1600x1200      60.0  
   1280x1024      60.0  
   1280x960       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
DP-1 connected 1080x1920+1920+0 left (normal left inverted right x axis y axis) 510mm x 287mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
```

I am out of ideas. Any help is greatly appreciated.

---

### Post by QIII on 2015-01-18
Regardless of the number of physical outputs, NVIDIA's site gives specifications that the adapter provides two active display channels.

So, in a "normal" arrangement you can only run two monitors.

However, since you have DisplayPorts, you might look into "daisy chaining" off of the DisplayPorts, but that requires DisplayPort 1.2.  You'll have to do some research on your equipment to see if that is supported.

---

