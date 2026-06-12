---
title: "CPU fan controller?"
date: 2006-11-20
forum: General Help
---

### Post by bhudda on 2006-11-20
Hello there. I was wondering if there are any apps that monitor system temp and also control fan speed? It seems as though my system is runnin full blown and the fan is spinning as fast as it can on bootup. Thanks a lot!

~b

---

### Post by Shatrat on 2006-11-21
> **bhudda said:**
> Hello there. I was wondering if there are any apps that monitor system temp and also control fan speed? It seems as though my system is runnin full blown and the fan is spinning as fast as it can on bootup. Thanks a lot!

~b
I'm not aware of any software methods for controlling CPU fans (and I wouldn't trust my CPU to one anyway).
There are hardware controllers out there that can be used to regulate the fan speed.  There is also lm-sensors which will show you your temps and fan RPMs (if your motherboard has the sensors but I think most do) at the command line.  There are several graphical system monitors that can display that data, im sure a little searching can dig up one you like if you're interested.

If you are using the retail heatsink/fan that came with your processor, the fan is probably not easily replaceable without getting a new heatsink as well.  If you have an aftermarket heatsink that accepts standard size 80mm or 92mm fans though, you could easily upgrade to a quieter model.

---

### Post by stream303 on 2006-11-21
What machine are you running?  Wouldn't happen to be a G5 iMac would it? :)  If so, see ya in the PPC forum!  (easy fix)

---

### Post by bhudda on 2006-11-21
> **stream303 said:**
> What machine are you running?  Wouldn't happen to be a G5 iMac would it? :)  If so, see ya in the PPC forum!  (easy fix)

O I only wish it were. If you have any extras...:rolleyes: 

Just a good old fashioned AMD64 I built myself a few years back. I think I do need to just do some hardware upgrading. The case itself is awful for air circulation, it has no actual case fans, and even in M$ it runs pretty hot. Thanks guys, I will live with it until I can buy new hardware. Since we are on this topic, what is a good case/mobo/pci-x combo that is out there for the AMD64? IF you know, heh!

~b

---

### Post by IanW on 2006-11-21
This _may_ work, it depends on whether your mobo supports pwm control via the fan headers. On my MSI K8N it'll only control the CPU & N/B fans.

[http://doc.gwos.org/index.php/Fancontrol]("http://doc.gwos.org/index.php/Fancontrol")

---

### Post by civetta on 2006-11-21
Have you tried changing the cpu frequency governor using cpufreq-selector?

Maybe by changing the governor, the cpu won't work so hard, and your fan will get a break! Find your current governor with

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor

---

### Post by jhenager on 2006-11-21
[http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
Looks promising.
[http://www.thinkwiki.org/wiki/ACPI_fan_control_script](http://www.thinkwiki.org/wiki/ACPI_fan_control_script)
This one is accompanied by a moderately scary warning:
ATTENTION!
These scripts rely on undocumented hardware features and override nominal hardware behavior. They may thus cause arbitrary damage to your laptop or data. Watch your temperatures!

---

### Post by rfruth on 2006-11-21
Does the BIOS offer any temperature monitoring / fan speed control ?  My Intel board does (ami bios) and its a low end motherboard :mrgreen:

---

