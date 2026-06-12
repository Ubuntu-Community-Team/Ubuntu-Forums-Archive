---
title: "Turn off laptop screen and turn on only with shortcut"
date: 2014-06-22
forum: General Help
---

### Post by cuentaparalinux on 2014-06-22
Dear users,
 
I'm running ubuntu 13.10 with xfce on my laptop. The problem is that I sometimes want to turn off the screen (without suspending or hibernating). I found out the command ```
xset dpms force off
``` and made a shortcut, but while it turns off the screen, whenever I touch the wireless mouse or move it, the screen inmediately turns on. I would like if someone can show me a script or something to turn off the screen with, let's say, CTRL+A and turn it on with only CTRL+A (not with mouse movement or by pushing other keyboard's buttons).

Hope you can help me. Thanks in advance. Regards.

---

### Post by jal9904 on 2014-06-23
Are you trying to sleep the laptop? Try following the instructions on [http://askubuntu.com/questions/22054/how-can-i-suspend-using-a-keyboard-shortcut-without-administrator-privileges](http://askubuntu.com/questions/22054/how-can-i-suspend-using-a-keyboard-shortcut-without-administrator-privileges) 


There is a software that lets you set a keyboard shortcut to sleep.

---

### Post by cuentaparalinux on 2014-06-23
Thanks jal9904 but I don't want to suspend, I just want to turn off the screen and turn it on again by only pushing a button (not by moving the mouse). Maybe I am not clear enough because english is not my mother tongue or maybe what I want sounds ridiculous but I like to read near my laptop and the brightness and light of the screen bothers me, that's why I want to turn it off...

---

### Post by Toz on 2014-06-23
Which backlight interfaces do you have? Run this command:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```...and post back the results.

Maybe we can just create a toggle script that turns the backlight on and off for you.

---

### Post by cuentaparalinux on 2014-06-23
Thanks a lot Toz! 
These are the results: 
```
 /sys/class/backlight/acpi_video0
9
95
9


 /sys/class/backlight/intel_backlight
665
4882
665

```

Regards!

---

### Post by Toz on 2014-06-23
Which of the following commands changes your brightness:
```
echo 50 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

..._**OR**_

```
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 665 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

...Note: you will be asked to enter your password so that you can affect the backlight interface.

---

### Post by cuentaparalinux on 2014-06-23
Thanks again Toz! Maybe it's odd but both commands change the brightness. The only difference I can see is that the second one "loses it's effect" when I increase the brightness by pressing the keyboard's button whereas the first one doesn't (I can't explain this better, sorry). Regards!

---

### Post by Toz on 2014-06-23
Okay then. Next step is to see if we can turn off the screen backlight. 

This next command will attempt to turn off the screen backlight, wait 5 seconds, then turn it back on again. Let me know if it works.
```
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness; sleep 5s; echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

If this works, we can script something. Interestingly, on one of my laptops this will turn off the screen backlight completely, on another it only dims it very lightly. Lets see what your does.

EDIT: If that doesn't blank your screen, can you post back the results of:
```
xrandr -q
```
...and we can try using xrandr next.

---

### Post by cuentaparalinux on 2014-06-24
Thank you very much for your help! 
The command ```
echo 0 | sudo tee /sys/class/backlight/acpi_video0/brightness; sleep 5s; echo 9 | sudo tee /sys/class/backlight/acpi_video0/brightness
``` only dims the screen very lightly. 
But I tried this (I wonder what happens with intel_backlight):
```
echo 0 | sudo tee /sys/class/backlight/intel_backlight/brightness; sleep 5s; echo 665 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` and it works like a charm!, the screen backlight is turned off completely. 

And here is the result of xrandr -q:

```
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 32767 x 32767LVDS1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 309mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

Regards!

---

### Post by Toz on 2014-06-24
And how about this command:
```
xrandr --output LVDS1 --off; read -n1; xrandr --output LVDS1 --auto
```

It should blank out the screen and wait for you to press a key on the keyboard to unblank it. See if that works. Try moving the mouse before pressing a key. It should stay blank.

---

### Post by cuentaparalinux on 2014-06-24
It works like a charm! That's exactly what I wanted! Thank you very much Toz! I don't want to steal your time, but how can I make a keyboard's shortcut with this command? Because I can make it work only in the terminal. Regards!

---

### Post by Toz on 2014-06-24
Simply create a [keyboard shortcut]("http://askubuntu.com/questions/331626/how-to-add-keyboard-shortcuts") for this command.

---

### Post by cuentaparalinux on 2014-06-24
EDITED: I could make the shortcut. Thank you very much Toz! I can study in peace now. Regards!

---

