---
title: "Changing Resoltuion"
date: 2021-09-22
forum: General Help
---

### Post by azah197 on 2021-09-22
Hi Guys,

Lenovo Ideapad 5 Pro 16:10
Hippo 21.04 OS


When I change the resolution of my display, i get a broken screen. ( I can't screenshot it, since the screenshot doens't show the broken screen)

My output for xrandr is 

Screen 0: minimum 16 x 16, current 2048 x 1280, maximum 32767 x 32767
XWAYLAND0 connected primary 2048x1280+0+0 (normal left inverted right x axis y axis) 340mm x 220mm
   2048x1280    119.92*+
   1600x1200    119.91  
   1440x1080    119.92  
   1400x1050    119.90  
   1280x1024    119.83  
   1280x960     119.89  
   1152x864     119.77  
   1024x768     119.80  
   800x600      119.85  
   640x480      119.52  
   320x240      117.34  
   1920x1200    119.90  
   1680x1050    119.89  
   1440x900     119.94  
   1280x800     119.85  
   720x480      119.65  
   640x400      119.64  
   320x200      117.55  
   2048x1152    119.96  
   1920x1080    119.93  
   1600x900     119.95  
   1368x768     119.83  
   1280x720     119.86  
   1024x576     119.85  
   864x486      119.69  
   720x400      119.54  
   640x350      119.24

Changing resoltion with xrandr gives me this output

xrandr --output XWAYLAND0 --mode 1920x1080
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  139 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  22
  Current serial number in output stream:  23

And also this one

xrandr --fb 1920x1200                     
xrandr: specified screen 1920x1200 not large enough for output XWAYLAND0 (2048x1280+0+0)
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  139 (RANDR)
  Minor opcode of failed request:  7 (RRSetScreenSize)
  Serial number of failed request:  22
  Current serial number in output stream:  23


Does someone know how to fix this or a workaround?

Ty!

---

### Post by TheFu on 2021-09-22
xrandr is for X/Windows.

You are using Wayland.  Use the Wayland tools.
[https://askubuntu.com/questions/973499/wayland-how-to-set-a-custom-resolution](https://askubuntu.com/questions/973499/wayland-how-to-set-a-custom-resolution)

[https://superuser.com/questions/1137574/manually-add-a-resolution-to-gnome-with-wayland](https://superuser.com/questions/1137574/manually-add-a-resolution-to-gnome-with-wayland)

---

