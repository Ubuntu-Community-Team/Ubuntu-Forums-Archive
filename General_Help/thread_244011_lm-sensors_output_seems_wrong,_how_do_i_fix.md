---
title: "lm-sensors output seems wrong, how do i fix?"
date: 2006-08-25
forum: General Help
---

### Post by Polygon on 2006-08-25
Ok so i just installed lm-sensors today using this guide: [http://www.ubuntuforums.org/showthread.php?t=2780](http://www.ubuntuforums.org/showthread.php?t=2780)

anyway, it shows that my motherbaord is 53 degrees C, and for the two cpu sensors (cpu intel and cpu amd, cant tell which one is right), they say thney they are at 32 degrees c (cpu intel) and 25 degrees C 

somehow this does NOT seem right, as in windows my cpu runs at about 64 degrees C, but i dont have anything to test the ubuntu lm-sensors output with

how do i check and possibly fix this lm-sensor output?

---

### Post by orb9220 on 2006-08-25
maybe the 53 is right and windows is more resource hungry therefore it would run Hotter?

---

### Post by Polygon on 2006-08-26
well, in both windows and ubuntu i run BOINC (for world community grid, kinda like folding at home), so my cpu is at 100% all the time, except that the BOINC client is the lowest priority so it doesnt slow down my computer

i would hightly doubt that ubuntu would be 30 degrees celesius cooler then in windows.. especially when both are running BOINC.

but i was looking around in a program in windows that diplays the temperature according to the sensors, and this is what i found:

[[IMG]http://img225.imageshack.us/img225/8421/windowstemperaturessht4.th.png[/IMG]](http://img225.imageshack.us/my.php?image=windowstemperaturessht4.png)

in the picture, it shows 53 degrees C (my motherboard) but then it also shows "Temp2" and "temp4", which is 25 and 32 degrees celsius, which is the exact temperature which ubuntu is reporting for my processor.

Im guessing that lm-sensors is confused and think that whatever "temp 2" and "temp 4" are cpus (hense cpu intel and cpu amd), but really they are hard drives or something, and lm-sensors is not reading the correct sensor for my real cpu, which is why the temperature is off

so... any suggestions on how to configure lm-sensor to use the correct sensor for my cpu?

---

### Post by Polygon on 2006-08-26
ok its wierd, right after a reboot, it seems that it discovered a new sensor, "temp" which very well be my processor, as its running at 53 degrees celsius. Very weird how it just appeared after a reboot.

edit: yes it is my processor.

---

### Post by insane_alien on 2006-08-26
sometimes it can be the actual sensor thats off. if i access the sensors(in any OS) it reads my CPU as running at 16000 centigrade. now, while a CPU that could handle these temps would be damn cool(parden the pun) this is not the case. my IR thermometer shows the heatsink to be a mere 40*C.

---

