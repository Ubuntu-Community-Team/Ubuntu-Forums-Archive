---
title: "FN-buttons work, but no actuall effect on brigthness"
date: 2014-05-24
forum: General Help
---

### Post by nestorarsenov on 2014-05-24
Hey,
I have Xubuntu on my netbook. All the button combinations of Fn + Fkeys used to work corectly, but few days ago I decided to do some power managment changes and I followed some advices on the internet, which I didn't understood (I'm a Linux noobie). Then I noticed that the shortcut for the screen brightness didn't worked anymore (in sense ABSOLUTLY nothing hapened when I pressed the combinations), but all the other FN-buttons-shortcuts still functioned (e.g. for the sound).
I searched for some info in the forum here. With the command "sudo apt-get install xbacklight" I managed that at least when pressing the brigthnes shortcut (Fn+F5 or Fn+F6) the light-bulb-icon appears, showing an increasing/decreasing bar. Anyway, there is no actual change in the real brigthnes of the screen, it's allways constant at about 80% of the total brigthnes.

I tried also the comand "xbacklight -set x" (with 1<x<100) but nothing happens, either.

So the summe up is: I changed something related with the Power Manager -> FN-buttons for brigthnes didn't worked -> "sudo apt-get install xbacklight" made the brightnes-bar appear again on the screen, but still no real brightness change.

Thanks for advices what I should do to get the control over the brigthnes back!

---

### Post by Toz on 2014-05-26
Hello and welcome to the forums.

> few days ago I decided to do some power managment changes and I followed some advices on the internet,
What were these changes that you made to your system?

What is the make and model of your netbook?

Can you open a terminal window, type in the following commands, and post back the results:
1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Info about your video card and driver:
```
lspci -k | grep -A2 VGA
```
3. Info about your backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

---

### Post by nestorarsenov on 2014-05-29
Hey guys,
thanks for the fast answer. 
Anyhow, I managed to fix the problem. I just needed do restart the netbook, afterwards the combinations for the backlight control worked just fine :/
Sorry for bothering.

---

