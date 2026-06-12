---
title: "Can't add a screen resolution"
date: 2012-12-04
forum: General Help
---

### Post by GameX2 on 2012-12-04
Hi,


I've just discovered an amazing script called "Newrez", which allow me to force any screen resolution (Up to 8000 pixels!!) on my laptop.  The main issue is that assuming I select a 1600x1200 resolution (I'm using 1366x768), my mouse remain stuck inside a 1366x768 rectangle.  This is a known problem, but I can't figure it out how to fix it.  I don't know how to use the script "Newrez-v" proprely.

I would like to add custom resolutions to Ubuntu, but that isn't working.  Here's the outpup of the command xrandr:

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192 LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm panning 1366x768+0+0    1366x768       60.0*+    1360x768       59.8     60.0      1024x768       60.0      800x600        60.3     56.2      640x480        59.9   VGA1 disconnected (normal left inverted right x axis y axis) HDMI1 disconnected (normal left inverted right x axis y axis) DP1 disconnected (normal left inverted right x axis y axis)   1600x1200_60.00 (0xd5)   83.5MHz         h: width  1280 start 1344 end 1480 total 1680 skew    0 clock   49.7KHz         v: height  800 start  801 end  804 total  828           clock   60.0Hz
```

Output of gtf 1280 800 60:

```
# 1600x1200 @ 60.00 Hz (GTF) hsync: 74.52 kHz; pclk: 160.96 MHz   Modeline "1600x1200_60.00"  160.96  1600 1704 1880 2160  1200 1201 1204 1242  -HSync +Vsync
```

So far, I've tried this:

```
xrandr --newmode "1600x1200_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
```
The terminal return nothing, no error, so I type this:

```
xrandr --addmode LVDS1 "1600x1200_60.00"
```
Now unfortunately, I keep getting this error.  I believe this is a known bug:

```
X Error of failed request:  BadMatch (invalid parameter attributes)   Major opcode of failed request:  150 (RANDR)   Minor opcode of failed request:  18 (RRAddOutputMode)   Serial number of failed request:  29   Current serial number in output stream:  30
```


Can you help?  What I am doing wrong, here?

Thank you very much!

---

### Post by dino99 on 2012-12-04
thats virtual fake :( you cant get more than your hardware can do

---

