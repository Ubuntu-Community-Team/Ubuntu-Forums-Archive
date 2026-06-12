---
title: "Headless 12.04 Only Displays 800x600 resolution in VNC!"
date: 2012-10-27
forum: General Help
---

### Post by Mesopotamia on 2012-10-27
Hi all,

My headless server running 12.04 only runs on 800x600 when I access it via VNC.

I use the built-in VNC server that comes with Ubuntu and I tried multiple other VNC servers with no luck.

Once I plug the server into a monitor and the monitor resolution is attained, I can get the exact same resolution as the monitor when I VNC into it!

The other problem I have is if the server plugged in into a monitor, the response of the VNC server (i.e. the Ubuntu machine) becomes sluggish and not responsive.

Could anybody please advise if they have tried headless servers with high resolution VNC access?

Thanks

---

### Post by cbraxton on 2012-10-27
Since a monitor is not detected the system defaults to a "lowest common denominator" resolution, so you need to use a suitable /etc/X11/xorg.conf file to get the results you want. The following is what I use on a headless server to get 1024x768 resolution. You would need to change the display driver at the top and mode at the bottom of the file to suit your own needs.

```

Section "Device"
Identifier	"Video0"
Driver		"ati"
EndSection

Section "Monitor"
Identifier "Monitor0"
VendorName "Monitor Vendor"
ModelName "Monitor Model"
Option "IgnoreEDID"
HorizSync 30.0 - 72.0
VertRefresh 50.0 - 160.0
EndSection

Section "Device"
Identifier "Default Device"
Option "NoLogo" "True"
Option "NoDDC" "True"
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Video0"
Monitor "Monitor0"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1024x768"
EndSubSection
EndSection

```

---

### Post by Mesopotamia on 2012-10-27
Hi cbraxton,

I don't have a 'xorg.conf' file under /etc/X11/ folder.

Am I supposed to create one?

I use the built-in Intel drivers on my motherboard so I haven't installed any drivers. Ubuntu detected those drivers automatically.

Thanks for the prompt response.

---

### Post by cbraxton on 2012-10-27
By default in modern versions of X11 there is no xorg.conf file and the system automatically probe the hardware to figure out what to do. If you create the file in the /etc/X11 directory it will be used to configure the display the way you want.

You're using whatever built-in driver X11 has figured out works for your hardware. You can find what this is by looking in the /var/log/Xorg.0.log log file and looking for the driver that is being loaded. I'm typing this on a laptop with an ATI/AMD graphics chip, so in the log I find the following:

```

Loading /usr/lib/xorg/modules/drivers/ati_drv.so

```

This matches up with the "Device" section in the xorg.conf file:

```

Section "Device"
Identifier	"Video0"
Driver		"ati"
EndSection 

```

X Window System configuration can be pretty complicated but there are plenty of examples available on the internet. You can also boot your system into text mode and generate an xorg.conf file by running "Xorg -configure" as root, this gives you something to start with that you can edit.

---

### Post by Mesopotamia on 2012-10-27
I created the xorg.conf file and added the driver in the 'Device' section but the PC still boots up with 800x600:

```
[    26.828] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
```

This is where I created the conf file:

```
xxxxx@Babylon:~$ sudo gedit /etc/X11/xorg.conf
```

And this is the 'Device' section setting in that file:

```
Section "Device"
Identifier	"Video0"
Driver "intel"
EndSection
```

Anything else I need to check to get this working?

Thanks again.

---

### Post by cbraxton on 2012-10-27
All I can think of is make sure the screen resolution that you want is the only resolution listed at the bottom of the file in the last Display subsection.

This works fine for me on Ubuntu 10.04, it is taken direct from a headless server that I can VNC into with the desired 1024x768 resolution displayed. I don't know if any changes have been made to X11 in 12.04 that would require a different xorg.conf configuration. 

You could also try hooking up a monitor, booting to a text-mode console, and running "Xorg -configure" as root to get what should be a working xorg.conf file to start with for your system.

---

### Post by Mesopotamia on 2012-10-28
> **cbraxton said:**
> All I can think of is make sure the screen resolution that you want is the only resolution listed at the bottom of the file in the last Display subsection.

It is.

> 
You could also try hooking up a monitor, booting to a text-mode console, and running "Xorg -configure" as root to get what should be a working xorg.conf file to start with for your system.

I will try that once I get a monitor to plug it to the server.

[B]Meanwhile, I would realy appreciate if someone have successfully run 12.04 on higher resolution than 800x600 on headless P could shed some light on this issue.
[/B]
Thanks

---

### Post by Mesopotamia on 2012-10-28
Anyone who could help? :)

---

### Post by Mesopotamia on 2012-10-28
Anybody? :)

---

### Post by Mesopotamia on 2012-10-31
Guys, anyone?

I can't believe no one uses headless 12.04 :)

---

### Post by Mesopotamia on 2012-11-01
Anybody who could help? :)

---

### Post by andrewbrown22 on 2013-01-15
Have you tried the "dummy" driver? I've been searching on this the majority of the day and I found it to work in my case. I'm using Ubuntu 12.04.1 on a Dell Optiplex with Intel graphics. 

Here's the link: [http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/](http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/)

(I found this on another UbuntuForums thread.. )

---

### Post by jkuzeja on 2013-06-28
This worked really well for me, and seems a lot simpler:

[http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html](http://www.ubuntugeek.com/how-change-display-resolution-settings-using-xrandr.html)

Here're the exact commands I used to get my headless box to 1920x1200.  My input is black, the command output is red.

[COLOR=#0000cd]administrator@server:$[/COLOR] xrandr
[COLOR=#ff0000]Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096[/COLOR]
[COLOR=#ff0000]VGA1 disconnected (normal left inverted right x axis y axis)[/COLOR]
[COLOR=#0000cd]administrator@server:$[/COLOR] cvt 1920 1200
[COLOR=#ff0000]# 1920x1200 59.88 Hz (CVT 2.30MA) hsync: 74.56 kHz; pclk: 193.25 MHz
Modeline "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
[/COLOR][COLOR=#0000cd]administrator@server:$[/COLOR] xrandr --newmode "1920x1200_60.00"  193.25  1920 2056 2256 2592  1200 1203 1209 1245 -hsync +vsync
[COLOR=#0000cd]administrator@server:$[/COLOR] xrandr --addmode VGA1 "1920x1200_60.00"
[COLOR=#0000cd]administrator@server:$[/COLOR] xrandr --output VGA1 --mode 1920x1200_60.00

And that did it.

---

