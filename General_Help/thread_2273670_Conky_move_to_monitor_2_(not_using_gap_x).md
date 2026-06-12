---
title: "Conky move to monitor 2 (not using gap_x)"
date: 2015-04-14
forum: General Help
---

### Post by devin11 on 2015-04-14
Hey there,

I have searched for the past 45min to find the answer on how to properly use the display setting and I have yet to find a single post where someone didnt say "just use gap_x". I have an issue with multiple monitors and no matter the video card or machine when I run conky it randomly chooses the monitor it thinks is the default display on startup. Sure I can sleep the script at startup but that is just a bandaid. With that said if I use gap_x 1920 it could either show up in the correct place or it could show up off right monitor viewport.

Any help would be appreciated

this is my xrandr --query output
```

Screen 0: minimum 8 x 8, current 3840 x 1080, maximum 8192 x 8192
DVI-I-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     59.9  
DVI-I-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 476mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1440x900       59.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1280x800       59.8  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     59.9  
HDMI-0 disconnected (normal left inverted right x axis y axis)

```

---

