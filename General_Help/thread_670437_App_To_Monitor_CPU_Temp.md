---
title: "App To Monitor CPU Temp"
date: 2008-01-17
forum: General Help
---

### Post by wsmoser2004 on 2008-01-17
I have an HP Pavilion zt3000 laptop, and I cannot find any programs that can monitor my CPU temperature.  I have a fairly common processor - Pentium M 1.7 GHz, so I'm not sure why it is a problem.  Most programs can determine my hard disk temperature, but I have only ever seen one that can see my CPU temperature - Hmonitor in Windows.  I believe I've tried pretty much everything - lm_sensors, gkrellm, ksensors, etc.  "sensors-detect" from lm_sensors reports that there are no sensors found, and /proc/acpi/thermal_zone is empty.

The Hmonitor program from Windows listed some numbers for the chipset and the "main sensor"...I am wondering if they might be useful to someone to write a driver for my temperature sensor.  I might be able to write something too, although I don't have much experience writing drivers.  If someone could point me in the right direction for resources on the topic, that would be great.

Or, if you've had some success with another temperature monitoring program I didn't mention, let me know and I'll try it :).

---

### Post by jeffus_il on 2008-01-17
Did you "sudo" sensors_detect?

From lm-sensors FAQ:

**Sensors says No sensors found![ ¶]("http://www.lm-sensors.org/wiki/FAQ/Chapter3#SensorssaysNosensorsfound")**

 [LIST]
[*]Did sensors-detect find sensors? (If not see Sensors-detect doesnt find any sensors)[/LIST][LIST]
[*]Did you do what sensors-detect said?[/LIST][LIST]
[*]Did you modprobe your sensor modules?[/LIST][LIST]
[*]Did you modprobe your I2C adapter modules?[/LIST][LIST]
[*]Did you modprobe i2c-isa if you have ISA sensor chips?[/LIST][LIST]
[*]Check lsmod.[/LIST]

---

### Post by wsmoser2004 on 2008-01-17
Yes, I did...because the first time I ran it, I didn't use "sudo" and it complained to me. :)

---

### Post by wsmoser2004 on 2008-01-28
Here are the numbers returned by Hmonitor.  I don't know what they mean, but hopefully they will be useful to somebody... :)

---

