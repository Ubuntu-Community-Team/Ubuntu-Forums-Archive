---
title: "stability issues"
date: 2016-08-25
forum: General Help
---

### Post by cee2 on 2016-08-25
i have been having stability issues the last 6 months maybe more.
Firefox was crashing alot
now qupzilla is crashing
windows 7 bsod after less than 6 hrs up and running

my system is mostly 5 yrs old  but the mobo at least has the good caps that dont swell with too much heat.
i bought a temp gun to test interior temps on the board
the back of the video card has temps around 65 celcius
the chipset has a hotspot of 75  c but mostly 65 around that hotspot
cpu is watercooled
other heatsinks on power chips near cpu are around 45 c or less as is rest of the mobo
750 watt enermax power supply is even cooler on the outside couldnt get interior reading

heres my hardware

Gigabyte 990XA-UD3 with 8 GB Corsair Vengence CMZ8GX3M2A1
PHENOM II 4 CORE 955 Black Edition cooled by Antec-Kuhler 920 Watercooler
RADEON HD 6870 lighting up; LG 34" & Acer 23" monitors plus 60"LED
ANTEC EarthPower 750W psu, Creative SB X-FI Extreme Music

ambient room temp is 24/25 c
i will check bios cpu temps after posting this

are these temps too high for longterm use and stability?
i think i have a 140 mm intake fan blowing in and  dual 120 sucking out of the casr thru water cooling rad plus the psu sucking air out
neither fan blowing out has hot air coming out , almost ambient

---

### Post by cee2 on 2016-08-25
bios says system temp is 34 c and cpu 47

---

### Post by cee2 on 2016-08-26
noone has any ideas?

---

### Post by QIII on 2016-08-26
GPUs run hot these days, so that temp does not strike me as unusual.  Your CPU temp, however, is of some concern.  It's actually higher than 47 degrees.  (I have an [article]("http://theleftcoastgeek.net/index.php/general-interest/5-lm-sensors-conky-and-amd-temperatures") on my blog discussing AMD CPU temps.)

On water, even an AIO, that temperature is far too high at idle.  You are almost certainly reaching 60 degrees under load.  That is the thermal limit on that CPU.  That means it will throttle, shut down or burn up.

The very first thing I would do is thoroughly check your cooling solution for proper installation and function.  One thing of note is that, given your fan arrangement, you probably have a negative case pressure situation.  You probably want to add another intake fan to get positive pressure in the case.  That will ensure the fans on your AIO are not starved of fresh, cool air.

---

### Post by cee2 on 2016-08-26
you might have a good point there, the 140 mm pushing in is a super quiet semi highflow fan which i think it running at full speed unless mobo is slowing it down but 
about 6 months before these problems started a smaller led lit  80 mm fan in the case window died.
It wasnt on hi speed most of its life so i kinda dismissed it usefulness but it did blow into the area just above the gpu, chipset,  in the general vr chip area that is still running the hottest.
i will look at replacing this one 80 mm
is there a way to ensure or lower the temps at which the mobo starts running its fans at full speed? the 140 intake and Antec Kuhler runs off mobo control too
cuz i checked and its not clear, theres auto, voltage and disabled...?

Also is there detailed instructions on how to install the antec kuhler controller software in a ubuntu system?

---

### Post by cee2 on 2016-08-26
maybe its not a hardware problem
i put a large house fan on the open side of the case and brought those hotspots literally down 20-30 degrees but firefox still crashed within an hour.
So unless theres permanent damage already its probly a software issue?
what do you think?

---

### Post by QIII on 2016-08-26
If blowing air in there keeps it cool, then it is a ventilation thing.  

It is possible that damage has been done, but that's by no means certain.  Try another browser or any app that will put a sustained load on the CPU (don't max it!) and see what happens.

---

