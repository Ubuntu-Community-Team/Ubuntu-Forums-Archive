---
title: "lm-sensors, how do I know which temperature it is reading?"
date: 2007-05-28
forum: General Help
---

### Post by foging on 2007-05-28
Hello!

I've succesfully installed lm-sensors without any problems. When I run >sensors part of my readout looks like this:

temp1:       +49°C  (high =   +56°C, hyst =  +107°C)   sensor = transistor           
temp2:     +29.5°C  (high =  +120°C, hyst =  +115°C)   sensor = diode

Now, how do I find out what temp1 and temp2 reads? I'm running my system on a VIA EPIA-EN12000EG mini-itx.

---

### Post by fanatik on 2007-05-29
i think you have to make an educated guess! looks like temp1 is cpu and temp2 is motherboard. you can rename them, look at /etc/sensors.conf, also have you seen this post: [http://ubuntuforums.org/showthread.php?t=2780]("http://ubuntuforums.org/showthread.php?t=2780")

---

