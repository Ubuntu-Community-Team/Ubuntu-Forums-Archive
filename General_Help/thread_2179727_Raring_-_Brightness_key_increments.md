---
title: "Raring - Brightness key increments"
date: 2013-10-09
forum: General Help
---

### Post by Taijitu on 2013-10-09
Hello UF :-).

I have a small question regarding the brightness keys.

In my system (Lenovo Thinkpad Edge S430, Ubuntu 13.04), they increase/decrease the backlight by 5 % on each press, but my backlight is controllable in much smaller increments, and I would like to change the behaviour of the buttons for that.

The brightness slider in the system settings can control the brightness in 1 % increments, so it is not because the driver does not support the higher resolution control.

Does anyone know if there is a config file somewhere defining the increase and decrease values of the buttons? Or any other proper way of doing this.

In advance, thank you.

Christofffer

---

### Post by varunendra on 2013-10-11
Not a "proper way", but I do have a "hacker's way" of doing it. But how do you know your System Settings applet adjusts in 1% increments? I'm on Ubuntu 12.04, and I don't see any indications anywhere to suggest exact value of increments. 

The only way for me to find out is to test (either by the slider or using Fn+ keys) and count (which tells me I have a total of 10 steps, thus 10% increment). This perfectly matches the min-max numerical values (0-10) acceptable to my **/sys/class/backlight/acpi_video0/brightness** file.

If you are sure you can adjust it in lesser increments, read the values in the relevant file after each increment, and you can set a script to do the increments/decrements with same values. You can then bind this script with a couple of "Hot Keys" using tools like "**xbindkeys**", so that you can control the brightness using those hotkeys.

But I doubt if you are going to get different values than what your Brightness keys are already offering. To confirm, you can use this script -
```
for i in `ls /sys/class/backlight/`; do echo -e "\n $i"; cat /sys/class/backlight/$i/{brightness,max_brightness,actual_brightness}; done
```
Run it when the brightness is at minimum. Then increment it (using your 1% slider) by one step and run the above code again. See which value changed, and by how much difference.

Repeat the same process with your Brightness keys and see if the increment difference actually differs. If it does, it maybe worth doing the script thing.

Post back the outputs here if they look confusing.

---

