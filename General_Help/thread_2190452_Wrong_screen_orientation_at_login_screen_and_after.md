---
title: "Wrong screen orientation at login screen and after login"
date: 2013-11-27
forum: General Help
---

### Post by daniel-holz91 on 2013-11-27
After upgrading to 13.10 the screen rotation with the acelerometer finally started to work on my Wetab. The only problem is that the screen orientation on the login screen and after the login is wrong. The screen is turned to right but the touchscreen isn't. I have to turn my Wetab to the right and back to normal again to get the correct screen orientation and a working touchscreen. After logging in the screen turns to the right again and I have to repeat these steps.

Is there any way to force the correct screen orientation?

Edit: Problem solved, workaround is described on my blog: [http://lackofalucidmind-en.blogspot.de/2014/06/wrong-screen-orientation-at-greeter-and.html](http://lackofalucidmind-en.blogspot.de/2014/06/wrong-screen-orientation-at-greeter-and.html)

---

### Post by heir4c on 2013-11-27
Look for the settings via SystemSettings>(under Hardware) 'Monitors' or 'Screens' (or something like that, I don't now in English, have a Dutch version).

---

### Post by daniel-holz91 on 2013-11-27
I already tried that without success. 
When I do my workaround to get the screen working the orientation is already set to normal. If I don't do my workaround and use a mouse the orientation is set to right. If I change it to normal everything is working fine but after a restart the problem comes back.

---

### Post by waterhead on 2013-12-21
I have the ExoPC vesion of this tablet (aka: Ciara Vibe). This problem has been perplexing me too.

I can set a screen/touchscreen/mouse orientation manually, by using xrandr and xinput commands in a bash script. I think if I could get this file to execute at boot, it might correct the problem. But, nothing I have tried solves this.

My script:

```
#!/bin/bash

xrandr --output LVDS1 --rotate normal
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController" "Evdev Axes Swap" 0
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController" "Evdev Axis Inversion" 0 0
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController Pen" "Evdev Axes Swap" 0
xinput set-prop --type=int --format=8 "eGalax Inc. USB TouchController Pen" "Evdev Axis Inversion" 0 0
xinput set-prop --type=int --format=8 4 "Evdev Axis Inversion" 0 0
```

---

### Post by waterhead on 2013-12-21
Upon further review:

Although a similar bash script worked in a different tablet, the xinput commands don't actually appear to change the touchscreen. The accelerometer is controlled by the asus_laptop module. This module appears to have mapped the accelerometer as a joystick, creating /dev/input/js0.

It also seems to be mapped as an input. running this command will list all of the events currently present:
```
cat /sys/class/input/input*/name
```

Running evtest on every event, I determined it is currenly mapped as event7:

```
sudo evtest /dev/input/event7
```

Still can't correct the default orientation.

---

### Post by waterhead on 2013-12-21
Well, it looks as if the method of rotating touchscreens has changed. Thanks for the tip from Anton in this bug report:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1103723](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/1103723)

He directs us to this page of the Ubuntu wiki:

[https://wiki.ubuntu.com/X/InputCoordinateTransformation](https://wiki.ubuntu.com/X/InputCoordinateTransformation)

So, I redid my script to this:

```
#!/bin/bash

xinput set-prop "eGalax Inc. USB TouchController" "Coordinate Transformation Matrix" 1 0 0 0 1 0 0 0 1
xinput set-prop --type=int --format=8 4 "Evdev Axis Inversion" 0 0
xrandr --output LVDS1 --rotate normal 
```

When run when the tablet is rotated in any orientation other than 'normal', this will switch everything to normal orientation.

I put a copy of it in my /etc folder, and then I added the path to the script in the /etc/rc.local file. But, it still has the same problem at login. But I feel that I may be one step closer.

Posted from my ExoPC tablet running Ubuntu 13.10

---

### Post by waterhead on 2013-12-23
More info:

It seems there was a somewhat recent patch to get the accelerometer on this tablet working:

[http://honk.sigxcpu.org/con/Accelerometer_and_screen_orientation_in_GNOME3.html](http://honk.sigxcpu.org/con/Accelerometer_and_screen_orientation_in_GNOME3.html)

It does seem to be controled by the gnome-settings-daemon. The patch that it refers to was added to udev version 204, which Ubuntu 13.10 has.

Running this command:

```
sudo gnome-settings-daemon --debug
```

Actually caused my screen to rotate to the right! I haven't found anything via the gsettings command where I could change this, but I will keep looking.

---

### Post by daniel-holz91 on 2013-12-29
Did you try to let LightDM run your scripts? Rc.local probably runs them before the x-server is even started.

This page describes how to run a script with LightDM. [URL="https://wiki.ubuntu.com/LightDM#Autorun_a_Command"]
https://wiki.ubuntu.com/LightDM#Autorun_a_Command[/URL]

Unfortunatly that didn't work for me but if you add 

```
xrandr --output LVDS1 --rotate normal 
```

to the autostart the screen won't rotate to the right after the login again.

---

### Post by waterhead on 2013-12-29
> **daniel-holz91 said:**
> Did you try to let LightDM run your scripts? Rc.local probably runs them before the x-server is even started.

This page describes how to run a script with LightDM. [URL="https://wiki.ubuntu.com/LightDM#Autorun_a_Command"]
https://wiki.ubuntu.com/LightDM#Autorun_a_Command[/URL]

I have tried that, but it still doesn't work. I do see it rotate to 'normal', then back to the right. There are some X options that can be added to the lightdm.conf file, but I can't find an example of how to use them.

> **daniel-holz91 said:**
> 

Unfortunatly that didn't work for me but if you add 

```
xrandr --output LVDS1 --rotate normal 
```

to the autostart the screen won't rotate to the right after the login again.

That I also have successfully used. But I really want to fix the login screen.

EDIT:
To see all of the available options that can be used in the lightdm.conf file, refer to this file:

/usr/share/doc/lightdm/lightdm.conf.gz

---

### Post by daniel-holz91 on 2013-12-29
[SIZE=2]Is there any way to disable the accelerometer at the greeter or to rotate the screen after the accelerometer turns it?
[/SIZE]

---

### Post by waterhead on 2013-12-29
I was thinking of something along this line. It is controlled by the asus_laptop module, but there are no module parameters available to control the accelerator.

```
modinfo asus_laptop
```

Maybe just blacklisting the module, and then doing a modprobe as an autostart script.

I can't work on it today. Gotta go to my Dad's, 50 miles away on icy roads!

---

### Post by daniel-holz91 on 2013-12-29
I tried blacklisting asus_laptop and it did disable the acelerometer but the screen still turns to the right at the login screen. Maybe gnome-settings-daemon is the problem.

---

### Post by waterhead on 2013-12-30
Looking at this, I found two possible settings:

```
gsettings get org.gnome.settings-daemon.plugins.xrandr default-configuration-file
'/etc/gnome-settings-daemon/xrandr/monitors.xml'
```

```
~$ gsettings get org.gnome.settings-daemon.plugins.xrandr default-monitors-setup
'follow-lid'
```

This raises twe questions:
1) There is no monitors.xml file. If we create one, what is the format?
2) What are the options other than 'follow-lid'?

---

### Post by daniel-holz91 on 2013-12-30
The folder /.config in your home-directory contains a monitors.xml-file. I already tried to copy it to /etc/gnome-settings-daemon/xrandr/ yesterday but nothing changed.

---

### Post by waterhead on 2013-12-30
Just a follow-up on my previous post.

A search found a monitors.xml file in my home directory, in the .config folder. I found that one of the configurations listed had an orientation of 'right' listed. I changed it to normal and saved it. I also copied the edited version to the /etc/gnome-settings-daemon/xrandr/ folder. A reboot showed nothing had changed. The monitors.xml file in my home folder is re-written on reboot.

I then edited the one in the /etc/gnome-settings-daemon/xrandr/ folder, and removed all configurations except for the LVDS1 display, since I know this is the primary display. Still no luck.

Edit: Brilliant minds think alike!!

---

### Post by daniel-holz91 on 2014-01-02
I didn't make much progress with this problem but I recognised something strange. If you have multiple workspaces and switch to an application which is on a different workspace there is a sliding animation and some kind preview picture of your workspaces. This preview is also rotated but I don't where it gets its monitor configuration.

---

### Post by waterhead on 2014-01-05
An update on what I have found.

If you delete the ~/.config/monitors.xml and monitors.xml.backup files, the screen orientation after login will be in the normal mode. A new monitors.xml file is not automatically created to replace the deleted ones.

I don't recall the orientation being a problem after the initial installation. It is something that came about later. I had already installed the CrystallHD drivers, and was trying to find a way to install the Chrontel driver for the HDMI output. Since I am running Ubuntu from an SD card, I tried a fresh installation. This time I installed it on a partitionon on the internal SSD. But, the orientation bug was there too, even without installing the CrystalHD driver. Maybe it is an update that breaks it.

With nothing to lose, I decided to install the daily-build of Ubuntu 14.04. That booted into the correct orientation on both the login screen and the user-session screen. But after a few boots, the user-session screen was rotated to the right (the login screen was still at normal). I then deleted the monitors.xml and monitors.xml.backup files, and it has booted both screens in normal mode ever since!

I'll use it a while before doing any hacking. I don't think anything uses the CrystalHD card by default. I can actually use this as a MythTV frontend, and the video is perfect using the Intel video driver.

---

### Post by daniel-holz91 on 2014-01-06
Let's hope that 14.04 stays free from this bug. I probably just wait for a more stable release of it and then upgrade to it.

---

### Post by daniel-holz91 on 2014-03-30
Installed 14.04 yesterday and applied your fix for greeter orientation problem today. Works perfectly, I'm asking myself why I didn't do this in 13.10 already. :D

---

### Post by vmalep on 2014-05-07
Dear all,

I have had this issue for a long time, and in my case, running an x220t (convertible thinkpad) that has no accelerator. Also, it still happens with the 14.04 version.

I believe it is a bug and I filled a bug report: [https://bugs.launchpad.net/ubuntu/+source/meta-gnome3/+bug/1316901](https://bugs.launchpad.net/ubuntu/+source/meta-gnome3/+bug/1316901)

For me, this happens if I rotate the screen with the rotation button of the thinkpad. This makes the screen rotate counter-clockwise (without rotating the touchscreen input) and generates the file monitor.xml in the .config folder.

The problem is that the line 13 of this monitor.xml file, that indicate the screen rotation, is modified during the login process (orientation is correct at the login prompt and has been modified once logged in...).

As said here above, to delete this file solve the issue.

Best regards,
Pierre

---

