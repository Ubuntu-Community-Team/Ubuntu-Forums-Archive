---
title: "WINE Workaraound for unsupported sensor chip?  Can't read CPU temperature!"
date: 2013-11-06
forum: General Help
---

### Post by morgan5 on 2013-11-06
Hi all,

I'm new to hardware, software, and Ubuntu in general so forgive me:

I built a new PC and running only Ubuntu 12.04. Processor: AMD A6 5400K Dual-core 3.6 Ghz.  Board: MSI FM2-A55M-E33.

As far as I can tell, everything is running great with one exception.  I cannot get a good read on CPU temp, fanspeed, etc. Apparently, lm-sensors does not support the sensor chip on my board.  Therefore, lm-sensors, psense, conky, etc. read zero degrees CPU temp mostly, with an occasional short-lived spike to 12-15 degrees. (I'm not located in Antarctica!)  No other sensors or fans are detected.  I've read through the boards for solutions, but apparently the (SuperI/O?) Fintek F71868AD sensor chip on this motherboard is not supported by lm-sensors.  (see: [http://comments.gmane.org/gmane.linu....sensors/3267]("http://comments.gmane.org/gmane.linux.drivers.sensors/32672")[http://comments.gmane.org/gmane.linu....sensors/32672]("http://comments.gmane.org/gmane.linux.drivers.sensors/32672"))

I can see what looks like an accurate temp reading of 42-ish when I'm in BIOS.

Question is, can I install and use WINE to run a free Windows-based app to monitor CPU temperatures, fan speed, etc.?  If so, which app should I use that is compatible with WINE?  I searched the WINE appdb in "Utilities" category -keywords sensor, monitor, CPU, and temperature  - and found only two apps both rated garbage (HWMonitor, and CPU-Z).

Thanks, and any other workaraounds or thoughts would be appreciated.

---

### Post by Bucky Ball on 2013-11-06
Installing the bulky Wine to run a dinky app to do this is radical and drastic action which I personally would only take if I couldn't live with only being able to see the temp in BIOS, but if that is your situation ... I'd wait and see if you get anymore responses here before leaping into this.

The main point is there's a fairly good chance your app won't work in Wine anyway. See here and search for it:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

PS: I just had a look in Synaptics and there seems to be a few other apps apart from lm-sensors. Some of them may be simply front-ends for it, though.

---

### Post by Mark Phelps on 2013-11-06
Wine probably will do no good because it can NOT be used to install drivers, and any app you run will have to rely on the Linux drivers to work.

You could check the version of lm-sensors you installed, if you did that using Software Manager or Synaptics.  There may be a newer version on their website, but if so, you would have to download and compile it yourself --  a lot of work just for temperature monitoring.

---

### Post by ian-weisser on 2013-11-06
> **morgan5 said:**
>  I've read through the boards for solutions, but apparently the (SuperI/O?) Fintek F71868AD sensor chip on this motherboard is not supported by lm-sensors.

Don't forget to file a bug against lm-sensors for this hardware, and to offer to help test possible solutions.

---

