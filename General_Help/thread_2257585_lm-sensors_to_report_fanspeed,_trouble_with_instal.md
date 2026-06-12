---
title: "lm-sensors to report fanspeed, trouble with install"
date: 2014-12-20
forum: General Help
---

### Post by idontknow2 on 2014-12-20
Hello guys. I've installed lubuntu 14.04 last night on my HP 450 Notebook PC and I've noticed that the fans aren't working. I'm trying to replicate the solution of kevbelisle here
[http://ubuntuforums.org/showthread.php?t=2002668&p=12024845#post12024845](http://ubuntuforums.org/showthread.php?t=2002668&p=12024845#post12024845)

I've downloaded the necessary files here and are now on my desktop.
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

What i got after doing those is 

```
user@computer:~/Desktop/New$ sudo make && sudo make install
[sudo] password for user: 
make[1]: Entering directory `/usr/src/linux-headers-3.13.0-43-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.13.0-43-generic'
test -d /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon || mkdir /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon
if test -f /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon/it87.ko -a ! -f /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon/it87_original.ko ; \
    then \
        cp -a /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon/it87.ko /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon/it87_original.ko ; \
    fi
cp it87.ko /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon
cp hwmon-vid.ko /lib/modules/3.13.0-43-generic/kernel/drivers/hwmon
cp: cannot stat &#8216;hwmon-vid.ko&#8217;: No such file or directory
make: *** [modules_install] Error 1


```

I'm bothered about this line
cp: cannot stat &#8216;hwmon-vid.ko&#8217;: No such file or directory

I've been working on this last night and a few hours this morning. Could someone break down the steps kevbelisle made?

Thanks.

---

