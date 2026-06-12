---
title: "FF and TB profiles on separate Hard Drive. Goes unresponsive for 30 seconds at times"
date: 2014-07-02
forum: General Help
---

### Post by 777funk on 2014-07-02
Through the day I notice sometimes everything else on the computer (all local programs) works fine but the two programs that have their data (profiles folder) on another hard drive go unresponsive almost as if that drive is sleeping or in power save mode for a second. Then once the data is called on again it continues as before. 

Is there anything I can do about this?

---

### Post by Toz on 2014-07-03
You can try to disable power-saving on that drive using hdparm. Something like:
```
sudo hdparm -B 255 /dev/sdX
```
...where /dev/sdX is the actual designation for that drive.

From "man hdparm":
```
       -B     Get/set Advanced Power Management feature, if the drive supports
              it.  A  low  value  means aggressive power management and a high
              value means better performance.  Possible  settings  range  from
              values  1  through  127 (which permit spin-down), and values 128
              through 254 (which do not permit spin-down).  The highest degree
              of  power  management  is  attained with a setting of 1, and the
              highest I/O performance with a setting of 254.  A value  of  255
              tells  hdparm to disable Advanced Power Management altogether on
              the drive (not all drives support disabling it, but most do).
```

---

