---
title: "How to correct 'waiting_for_supplier' issue on dtoverlays/*.dtbo"
date: 2022-08-30
forum: General Help
---

### Post by tc2020 on 2022-08-30
Hello,

I am upgrading from Ubuntu 20.04LTS (kernel 5.4.0) to 22.04LTS (kernel  5.15.0) on RPi4. I use the same *.dtbo files without recompiling and  they work, except an eeprom on i2c-1 bus which has a few devices on it.  The following lists the details:

```
$ sudo ls -l /sys/class/i2c-dev/i2c-1/device/1-0050 total 0
-r--r--r-- 1 root root 4096 Aug 30 14:06 modalias
-r--r--r-- 1 root root 4096 Aug 30 13:59 name
lrwxrwxrwx 1 root root    0 Aug 30 14:06 of_node -> ../../../../../../firmware/devicetree/base/soc/i2c@7e804000/eeprom@50
drwxr-xr-x 2 root root    0 Aug 30 14:06 power
lrwxrwxrwx 1 root root    0 Aug 30 13:59 subsystem -> ../../../../../../bus/i2c
-rw-r--r-- 1 root root 4096 Dec 31  1969 uevent
-r--r--r-- 1 root root 4096 Aug 30 14:06 waiting_for_supplier 

```

With the older kernel version, it works and displays the following for AT24 eeprom type:

 ```
$ sudo ls -l /sys/class/i2c-dev/i2c-1/device/1-0050 total 0
drwxr-xr-x 3 root root    0 Aug 29 17:11 1-00500
lrwxrwxrwx 1 root root    0 Aug 30 01:09 driver -> ../../../../../../bus/i2c/drivers/at24
-rw------- 1 root root  256 Aug 29 17:11 eeprom
-r--r--r-- 1 root root 4096 Aug 30 01:09 modalias
-r--r--r-- 1 root root 4096 Aug 29 17:11 name
lrwxrwxrwx 1 root root    0 Aug 30 01:09 of_node -> ../../../../../../firmware/devicetree/base/soc/i2c@7e804000/eeprom@50
drwxr-xr-x 2 root root    0 Aug 30 01:09 power
lrwxrwxrwx 1 root root    0 Dec 31  1969 subsystem -> ../../../../../../bus/i2c
-rw-r--r-- 1 root root 4096 Dec 31  1969 uevent 

```

What is 'waiting_for_supplier' attribute in the newer kernel as  shown?. What is it that it is waiting to load driver (at24)?. How do I  correct this?.

Any help would be greatly appreciated. Thank you.

---

