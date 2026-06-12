---
title: "Low Resolution After Power Outage - Ubuntu Mate 17.04"
date: 2017-11-03
forum: General Help
---

### Post by riehlg on 2017-11-03
[COLOR=#333333][FONT=Ubuntu]So the power went out at my house and my laptop shut down because the battery in it is no longer functioning. After starting my computer up when the power came back on, my resolution is low and I cannot switch it back. I'm stuck at 1024x768 instead of the 1600x900 it always runs at. Everything is fine if I boot into Windows but in Ubuntu Mate I can't change the resolution.

EDIT: The computer is a Lenovo T420 with Intel HD3000 graphics.

Here's my output of xrandr

[/FONT][/COLOR]```
greg@greg-pc:~$ xrandrxrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00* 
  1600x900_60.00 (0x28f) 118.250MHz -HSync +VSync
        h: width  1600 start 1696 end 1856 total 2112 skew    0 clock  55.99KHz
        v: height  900 start  903 end  908 total  934           clock  59.95Hz

```[COLOR=#333333][FONT=Ubuntu]

And here's cvt 1600 900

[/FONT][/COLOR]```
greg@greg-pc:~$ cvt 1600 900
# 1600x900 59.95 Hz (CVT 1.44M9) hsync: 55.99 kHz; pclk: 118.25 MHz
Modeline "1600x900_60.00"  118.25  1600 1696 1856 2112  900 903 908 934 -hsync +vsync
```

---

### Post by mörgæs on 2017-11-04
HI, welcome to the fora.

First you should consider how much effort you want to put into saving a 17.04 installation. Within two to three months you need to let it go anyway and install 17.10. 

If it were my computer I would use the the occasion and do a clean install of Mate 17.10 now.

---

### Post by riehlg on 2017-11-06
Hey, thanks for the response. I hadn't realized that 17.10 was out and I was going to test things out in a live CD and when I went to download it, I saw 17.10. I just did the sudo do-release-upgrade and upgraded to 17.10. Everything is working perfectly again. I'm guessing that the upgrade ended up overwriting whatever file got corrupted. I don't have anything really saved on my Linux partition (everything is on a 2nd drive in my laptop) so if something gets borked, I'll just do a clean install.

---

