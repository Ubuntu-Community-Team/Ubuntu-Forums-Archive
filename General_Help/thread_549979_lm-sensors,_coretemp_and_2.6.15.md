---
title: "lm-sensors, coretemp and 2.6.15"
date: 2007-09-13
forum: General Help
---

### Post by wachaca on 2007-09-13
Hello,
I am using  kernel 2.6.15-29-server on an Intel D946GZIS motherboard

In theory my MB/CPU is compatible with the list at
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

Running the latest sensors-detect as per instructions at
[http://www.lm-sensors.org/wiki/iwizard/NoSensorsDetected](http://www.lm-sensors.org/wiki/iwizard/NoSensorsDetected)

I get the following 
> 
#----cut here----
# I2C adapter drivers
modprobe i2c-i801
# Chip drivers
# no driver for Andigilog aSC7611 yet
# Warning: the required module coretemp is not currently installed
# on your system. For status of 2.6 kernel ports check
# [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices). If driver is built
# into the kernel, or unavailable, comment out the following line.
modprobe coretemp
# sleep 2 # optional
/usr/bin/sensors -s # recommended
#----cut here----


modprobe coretemp fails, indicating that the module does not exist.

Looking around in the forums I see that many people upgraded to 2.6.22 just to solve this.

Is there a way to solve this without changing the kernel?

I built a 2U server with this board and I need to keep an eye on the CPU/MB to make sure the ventilation that I placed is enough.

Thanks
Wachaca

---

