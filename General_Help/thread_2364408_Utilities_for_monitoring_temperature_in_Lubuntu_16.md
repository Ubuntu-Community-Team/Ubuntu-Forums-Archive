---
title: "Utilities for monitoring temperature in Lubuntu 16.04.2 LTS?"
date: 2017-06-22
forum: General Help
---

### Post by AbleTassie on 2017-06-22
Hello all,

My laptop shut off suddenly without warning, It has never done that before. I had another older laptop that did that several times in the past and it was from overheating. I am wondering what utility to use to monitor temperature. I've already downloaded and installed Psensor and Xsensors. I am wondering if there are other utilities for monitoring temps for this operating system (Lubuntu 16.04.2 LTS) as well. I will attempt to use an Intel forum to check on normal operating temperatures. The CPU is an Intel processor.

In addition to shutting off suddenly, the time and date clock has now changed to an incorrect date and time. I have reset it manually, but it reverts back to the same incorrect date and time when I restart the computer. I seem to be unable to get the date and time to automatically sync off the internet.

  And the battery (which is old) also no longer seems to be holding a charge.

Thanks,

A.

---

### Post by papibe on 2017-06-22
Hi AbleTassie.

I use terminal commands to monitor CPU and GPU temperatures.
```
sudo apt-get install lm-sensors
```
Then
```
$ sensors | grep Core
Core 0:       +61.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:       +61.0°C  (high = +84.0°C, crit = +100.0°C)
Core 2:       +61.0°C  (high = +84.0°C, crit = +100.0°C)
Core 3:       +61.0°C  (high = +84.0°C, crit = +100.0°C)
```
In order to monitor the temperature on a terminal you could do:
```
watch -n 15 'sensors | grep Core'
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by vasa1 on 2017-06-22
If you just want an indicator, lxpanel has a temperature monitor.

Right-click on the panel, Add/Remove Panel Items, and take it from there. Look for "Temperature Monitor". It should work "out of the box".

BTW, please ask just one specific issue per thread. Otherwise, things could get a bit chaotic. Thanks!

---

### Post by AbleTassie on 2017-06-23
Thanks, papibe, I will try lm-sensos. Do you know how lm-sensors arrives at a critical temp? Is it actually hardware dependent? 

Thanks vasa1: I added the panel temperature. It reads the same as core 0 in Psensor. 

The reason I included the other issues in my original post is because I thought they might all be related. That is, that the sudden shut-off (due possibly to hi temperature) might have changed the date & time and it might also be related to the battery somehow.

A.

---

### Post by dragonfly41 on 2017-06-23
GKrellM System Monitor (in Software Centre) has some nice features and can be customised by adding plugins.

There is also a server version for monitoring servers.

---

### Post by CatKiller on 2017-06-23
I use Conky to display, amongst other things, my temperatures.

---

### Post by papibe on 2017-06-23
> **AbleTassie said:**
> Do you know how lm-sensors arrives at a critical temp? Is it actually hardware dependent? 
As far as I can tell, yes.

Either when you install it, or at first run, it will run a lot of auto hardware detection. Once the chip is detected, my guess is the 'high' and 'critical' temps are obtained from predefined data located at the config file (/etc/sensors3.conf).

Regards.

---

### Post by AbleTassie on 2017-06-27
Hi papibe, vasa, Cat, and dragon,

I installed lm-sensors and also called Intel. Intel told me that in general as long as a CPU is under 80 degrees C then you are ok. They suggested contacting Lenovo, but due to a snafu, I was not able to join a Lenovo forum.

 With three online videos running at the same time & ambient temp up to about 74 F, I get up close to 75 C.  My laptop is up on bottle caps now (fastened to the PC with velcro). The P-sensor gives me the same temps for core 0 and core 1 as lm-sensors; and lm-sensors gives a critical temp of 85 C for cores 0 & 1, so that is another 5 degrees I can go up. And the PC has not shut off spontaneously any more. So I guess I am OK.

I will mark this thread as SOLVED.

THANKS TO ALL. :p

A.

---

### Post by papibe on 2017-06-27
Great to hear that :)

Some of those cooling pads are very good. Recently I got one that reduces about 10C in average.

Just a thought.
Regards.

---

