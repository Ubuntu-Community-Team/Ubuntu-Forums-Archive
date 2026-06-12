---
title: "Toshiba NB250, resolution unavailable"
date: 2014-06-20
forum: General Help
---

### Post by cristi5 on 2014-06-20
Hello.
 I have a toshiba NB250 small notebook and I am using the vga video output to a 22 inch monitor.
 In system settings I only have two options: 800X600 and 1024X768 but the monitor supports really large resolutions. 
 How can make a higher resolution available ? 
 The video card is Intel GMA 3150 and from what I've googled ubuntu already has the latest drivers (I update ubuntu everytime).

Thanks

---

### Post by papibe on 2014-06-20
Hi cristi5. Welcome to the forum ):P

Could you open a terminal, run these commands, and post back the results (you can copy/paste the text)?
```
lspci -nnk | grep -iA2 vga

xrandr -q

xrandr -q --q1
```
Regards.

---

### Post by kostkon on 2014-06-21
Be aware that GMA3150 can only go up to 1680x1050 on external monitors; the OEM may have set the maximum external resolution even lower, mine (HP netbook) is at 1600x900@60Hz, yours according to [this page]("http://www.toshiba.co.uk/discontinued-products/toshiba-nb250-107/") is only 1400x1050@85Hz. In other words, you cannot go higher than that I'm afraid.

I'm not really sure why 1400x1050 is not being listed as available. I'm guessing your monitor probably does not support that mode, i.e. either 1400x1050@85Hz or at least 1400x1050@60Hz, I could be wrong though.

Hope that helps.

---

### Post by cristi5 on 2014-06-22
Thank you. 
This is the output of the commands : 
crist@troaca:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller [8086:a011]
	Subsystem: Toshiba America Info Systems Device [1179:ff60]
	Kernel driver in use: i915
crist@troaca:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1024x600       60.0 +
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0* 
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
crist@troaca:~$ xrandr -q --q1
 SZ:    Pixels          Physical       Refresh
*0   1024 x 768    ( 271mm x 203mm )  *60  
 1    800 x 600    ( 271mm x 203mm )   60   56  
 2    848 x 480    ( 271mm x 203mm )   60  
 3    640 x 480    ( 271mm x 203mm )   60  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis

---

### Post by cristi5 on 2014-06-22
found this and it works : 
[http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768](http://askubuntu.com/questions/13783/external-monitor-resolution-doesnt-go-above-1024x768)

---

