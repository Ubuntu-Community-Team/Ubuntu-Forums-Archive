---
title: "Refresh rate, Nvidia 9600GT, 13.10"
date: 2014-03-10
forum: General Help
---

### Post by Steven_Parker on 2014-03-10
Hello guys, To start I am having issues setting my monitor settings up correctly. I have a Nvidia 9600GT connected to a IBM P275 CRT Trinitron monitor, and a Viewsonic LCD. The IBM is set to 1600x1200 and the LCD at 1680x1050. My issue is Ubuntu will only allow me a max refresh rate for my CRT at 85hz. Is there a way to force it to a higher value? In windows I have the same issue but I can bypass it by creating a custom .INF monitor driver and set my own custom resolution of 1600x1200_100hz. I have tried "xrandr -r 100" but get an error "Rate 100.0 Hz not available for this size." Im assuming that is due to the monitors default EIDE value? any thoughts or imput on this issue would be wonderful. thanks guys :D

Xrandr command:
Screen 0: minimum 8 x 8, current 3280 x 1200, maximum 8192 x 8192
DVI-I-0 connected primary 1600x1200+1680+0 (normal left inverted right x axis y axis) 388mm x 291mm
   1600x1200      85.0*+   75.0     70.0     65.0     60.0  
   2048x1536      75.0     60.0  
   1920x1440      75.0     60.0  
   1920x1200      60.0  
   1920x1080      59.9  
   1856x1392      75.0     60.0  
   1792x1344      75.0     60.0  
   1680x1050      84.9     74.9     69.9     60.0     59.9  
   1440x900       59.9  
   1400x1050      85.0     74.8     70.0     60.0  
   1360x768       60.0     59.8  
   1280x1024      85.0     75.0     60.0  
   1280x960       85.0     60.0  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     87.1     75.0     70.1     60.0  
   960x600        60.0  
   960x540        60.0  
   840x525        85.0     75.0     69.9     60.0     59.9  
   832x624        74.6  
   800x600        85.1     85.1     75.0     72.2     60.3     56.2  
   720x450        59.9  
   720x400        85.0  
   700x525        74.8     60.0  
   680x384        60.0     59.8  
   640x480        85.0     75.0     72.8     72.8     59.9  
   640x400        85.1  
   640x350        85.1  
   512x384        70.1     87.1     60.0  
   400x300        72.2  
   320x240        72.8     60.1  
   320x175        85.3  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
TV-0 disconnected (normal left inverted right x axis y axis)
DVI-I-2 disconnected (normal left inverted right x axis y axis)
DVI-I-3 connected 1680x1050+0+150 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+   74.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
   640x400        70.1

---

### Post by Frogs Hair on 2014-03-10
> I'm assuming that is due to the monitors default EIDE value? I think this correct . With my Nvidia desktop the Nvidia Xserver Settings  always detect and display the native resolution and refresh rate which I know to be correct for my monitor . I was unable to find this information for your monitor.

---

### Post by Steven_Parker on 2014-03-10
well thats the thing with CRT screens though. Especially Trinitrons. the EIDE sets a max safe refresh rate of 85hz at 1600x1200 but in reality this monitor can do 100+hz at that res. For instance in windows I have a custom res for 800x600@160hz for CS and CSS, and 1600x1200@100hz for my desktop. I would love to do this with Ubuntu.

---

### Post by Frogs Hair on 2014-03-12
You may want to search for simalar posts. [http://askubuntu.com/questions/147580/how-to-see-change-screen-refresh-rate](http://askubuntu.com/questions/147580/how-to-see-change-screen-refresh-rate)

---

### Post by Steven_Parker on 2014-03-12
Ty for the post but my issue is, according to xrandr my max refresh rate at 1600x1200 is 85. It wont let me go any higher than that, but my monitor can handle a max of 104hz refresh at that resolution. As a gamer in linux having the highest possible refresh rate is very importaint to me. In windows I have 2 custom resolution settings set by making my own monitor .INF driver to allow 160hz refresh at 800x600 and 104hz at 1600x1200. My issue is no matter what I select it will not let me go higher than 85hz because xrandr only sees the max of 85hz designated from my monitors EIDE. I first need to find a way to bypass the EIDE or create a new EIDE for the screen. I am new with linux "2-3 days expierience" and have no clue where to start.

---

### Post by Steven_Parker on 2014-03-12
Another quick question, using compizconfig-settings-manager to manually set the refresh rate, Is it possible to set 2 seperate refresh rates for 2 different screens? Keep in mind im using 2 screens on my setup, one LCD at 60z and one trinitron CRT trying to get 104hz. If I set 104hz on one screen will it try to set that refresh on my second screen as well?

-Edit: The compizconfig-settings-manager method did not work as did using "xrandr -r 100" I get the message "Rate 100.0 Hz not available for this size"

---

### Post by Steven_Parker on 2014-03-15
-Bump

---

