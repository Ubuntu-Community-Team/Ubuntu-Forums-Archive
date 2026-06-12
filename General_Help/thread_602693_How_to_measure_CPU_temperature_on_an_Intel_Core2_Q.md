---
title: "How to measure CPU temperature on an Intel Core2 Quad"
date: 2007-11-04
forum: General Help
---

### Post by ryke on 2007-11-04
Hi,

I would like to find some command to measure my CPU temperature (Iwould like to add it to a screenlet)

I'v tried some of them in a Terminal (cat /proc/acpi/thermal_zone/THRM/temperature, cat temperature, acpi -tB) but none of them work. I'v tried some panel applets but no success, too.

(I'm using gutsy. The 4 processors are recognized in the System Monitor)

Thanx in advance ;)

---

### Post by Waappu on 2007-11-04
Hi

I have used lm-sensors, you can find it from repos also
[http://www.lm-sensors.org/](http://www.lm-sensors.org/)

---

### Post by floke on 2007-11-04
Terminal: use

acpi -t

or

watch acpi -V

---

### Post by ryke on 2007-11-04
Thanx for your answers

The package lm-sensor I've had already installed.

I had already tried first command... I've tried the second one, but no success.

The message from Terminal is:
No support for device type: thermal

Regards

---

### Post by Waappu on 2007-11-04
> **ryke said:**
> Thanx for your answers

The package lm-sensor I've had already installed.

I had already tried first command... I've tried the second one, but no success.

The message from Terminal is:
No support for device type: thermal

Regards
Hi

run command ```
sudo sensors-detect
``` and add modules to ```
/etc/modules
```

---

### Post by ryke on 2007-11-04
Hi, it works ! :)

In fact, I have not found a command from Terminal to measure the temperature, but with an applet, I have now in my panel a very nice 4 icons showing the temperature for the 4 processors ;)

Thanks for your help

---

### Post by minus198 on 2007-11-04
sudo apt-get install lm-sensors 

sudo sensors-detect 

sudo modpprobe "the modules that you got from 'sensors-detect"

sensors

---

### Post by ryke on 2007-11-04
perfect ! now I have all the options :)

thank you !!

---

### Post by gauthamnaggg on 2008-02-25
Visit the following link and follow the instructions specified in the link.This works for me .I hope  this will work for u also

:guitar:[http://www.go2linux.org/lm-sensors-ubuntu](http://www.go2linux.org/lm-sensors-ubuntu)

---

