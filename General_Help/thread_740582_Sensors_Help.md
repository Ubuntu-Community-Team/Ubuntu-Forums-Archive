---
title: "Sensors Help"
date: 2008-03-30
forum: General Help
---

### Post by kuja on 2008-03-30
I can't seem to get lm-sensors to work on this desktop or may laptop. lm-sennsors said that it couldn't find any sensors.I can see temps in bios so there must be sensors .... I can't seem to get coretemp to work either ( I tried modprobing it on a hunch, but it said no devices found). The motherboard is an Intel DX38BT and the CPU is a Core 2 Q9300.

---

### Post by chewearn on 2008-03-31
Just throw it out there; have you run:
```
sudo sensors-detect
```

---

### Post by kuja on 2008-04-01
Well, seems to be working in Hardy on my laptop (didn't work in Gutsy or Feisty) - but only displays CPU temp, not sure if it has any other sensors though so it should be okay. I'm honestly more interested in my desktop though, which doesn't seem to have any luck at all as of yet. It says this:

"Sorry, no sensors were detected.
Either your sensors are not supported or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ) 
(FAQ #4,24,3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

My board has Intel x38 northbridge and IC9R southrbridge IIRC.


Given this info, now that I've looked at that extra R a little closer, perhaps lmsensors supports ICH9 and not ICH9R. Maybe I'm out of luck for the time being. Guess it's what i get for using such a new board.

---

