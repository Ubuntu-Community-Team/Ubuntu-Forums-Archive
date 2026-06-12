---
title: "Ubuntu switches to Console Mode After TV Input switchback"
date: 2013-02-24
forum: General Help
---

### Post by todd.seidenberg@gmail.com on 2013-02-24
Hi, 

I have a Laptop on a docking station, running UBUNTU 12.10. I currently have the DVI out of the docking station connected to my HDTV, and I can happily display X at HD 1920x1080 resolution. 

I am currently running Fluxbox, and this launches XBMC. 


When the TV is set to the input that points to the UBUNTU machine, everything is good.  I load up the OS. X starts without an issue. 


However - when I switch TV inputs (perhaps to my Satellite receiver) and then switch BACK to my UBUNTU machine, X dumps me into console mode. All I see is text - specifically the text of the last bootup messages before X started.  

I have noticed that the X is still running in the background. A  ps command yields that. 

The only thing thing I've been able to do to get out of it is reboot. Which is sub-optimal. 

I did notice that if I disable DRI in my X configuration, this problem goes away. But then the speed of the display is VERY bad - the responsiveness of XBMC, specifically is slow. 



I kick of xrandr at boot with the following: 


```
xrandr --output DVI1 --auto --mode 1920x1080 && xrandr --output LVDS1 --off

```

I also notice that when I DON'T use xrandr i don't experience this problem. But then I have the problem where my display shows up on my laptop, even if its closed, AS WELL as the HDTV. This of course makes the system run much hotter.  

So I like the control that xrandr is giving me, so I'd like to be able to keep using it. 

Does anyone have any idea what I can do in this situation? 


- Thanks,

Todd

---

