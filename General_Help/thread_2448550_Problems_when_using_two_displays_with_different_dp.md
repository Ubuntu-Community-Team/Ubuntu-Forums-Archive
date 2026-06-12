---
title: "Problems when using two displays with different dpi"
date: 2020-08-09
forum: General Help
---

### Post by jed351 on 2020-08-09
Hi everyone, 
 
I am very new to Linux and recently experimenting with Ubuntu 20.04. 

I have a laptop with a 3840x2160 display (ePD-1-1) and a 1920x1080 external display (HDMI-1-1) on the laptop's left hand side. I was trying the scale the internal display by 200% and the external display by 100% using the setting GUI. However, both displays ended up scaling by the same number. It is simply unusable because it is either both in 100% or 200%.

I then attempted using xrandr in the terminal.

```
xrandr --dpi 270 --fb 7680x2160 --output  eDP-1-1 --mode 3840x2160 --right-of HDMI-1-1  --output HDMI-1-1 --scale 2x2 --pos 0x0 
```

Unfortunately, my external display (HDMI-1-1) is now using the entire pannel to display 1/4 of what it is suppose to show. Thus means --scale is not scalling.

[IMG]https://i.stack.imgur.com/QUvWY.png[/IMG] 
picture sourced from a person encountering the same problem [https://askubuntu.com/questions/1228634/external-monitor-scaled-by-xrandr-only-shows-1-4-of-what-its-supposed-to-show](https://askubuntu.com/questions/1228634/external-monitor-scaled-by-xrandr-only-shows-1-4-of-what-its-supposed-to-show)


I also attempted to add ```
 --panning 3840x2160+2160+0 
``` 

But I got this in return:

```
X Error of failed request:  BadMatch (invalid parameter attributes)  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  29 (RRSetPanning)
  Serial number of failed request:  36
  Current serial number in output stream:  36

```

Is there anything else that I could try or something that I did wrongly?
Thx

---

