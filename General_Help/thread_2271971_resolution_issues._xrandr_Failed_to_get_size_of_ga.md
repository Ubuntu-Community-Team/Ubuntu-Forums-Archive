---
title: "resolution issues. xrandr: Failed to get size of gamma for output default?"
date: 2015-04-03
forum: General Help
---

### Post by laurence2 on 2015-04-03
Hi

I'm using a beta of ubuntu-gnome 15.04 fully updated with all the packages from the repositories.

I have an asus laptop with an AMD A6-3400 APU and a screen with a native resolution of 1366x768, in the live image this works great. 

However after installation things did not work so well, in order to get to any kind of desktop I had to add redeon.modeset=0, this eventually gets me to a desktop with a terrible resolution (1024x768). any attempt to boot to ubuntu without this results in a black screen.

xrandr and attempts to ad modes with it do not work
```
loz@centrefuge:~$ xrandrxrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
loz@centrefuge:~$ xrandr --addmode default  1366x768_60.00
xrandr: Failed to get size of gamma for output default
xrandr: cannot find mode "1366x768_60.00"
loz@centrefuge:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 



```


There is currently no xorg.conf file.

Attempts to install fglrx result in black screen issues that I can seem to get around with either radeon.modeset=0 or nomodeset added to the appropriate grub lines meaning that i have to drop to the recovery console and remove fglrx and wind back the changes as follows

> $ sudo apt-get purge 'fglrx*'
$ sudo update-alternatives --remove-all x86_64-linux-gnu_gl_conf
$ sudo apt-get install --reinstall libgl1-mesa-dri libgl1-mesa-glx

I'm not sure what to try next to get a decent resolution...

Anyone got any good suggestions?

---

### Post by laurence2 on 2015-04-04
Can anyone help here, updated title to hopefully attract someone who knows the answer....

---

### Post by laurence2 on 2015-04-05
xorg log file here:
[http://paste.ubuntu.com/10742864/](http://paste.ubuntu.com/10742864/)


Also maybe this will help
> lspci -nn | grep VGA

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647]

> loz@centrefuge:~$ xrandr --newmode "1368x768_60.00"   85.25  1368 1440 1576 1784  768 771 781 798 -hsync +vsyncxrandr: Failed to get size of gamma for output default
X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  19
  Current serial number in output stream:  19




lsmod output here:
[http://paste.ubuntu.com/10742912/](http://paste.ubuntu.com/10742912/)

---

