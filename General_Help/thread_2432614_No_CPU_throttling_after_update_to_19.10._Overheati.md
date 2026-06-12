---
title: "No CPU throttling after update to 19.10. Overheating instead."
date: 2019-12-05
forum: General Help
---

### Post by xaxazak on 2019-12-05
When I place my system under load, my CPU cores keep getting hotter  until I get a PC speaker alarm at 90 degrees (temperatures checked via  psensor).
thermald seems to be running, but I don't think it's throttling - I don't see any messages via dmesg (is that where I should look?).


This has been a problem since updating to Xubuntu 19.10. Xubuntu 19.04 had no thermal issues.

_**Specs:**_
OS: xubuntu 19.10
Kernel: Linux 5.3.0-23-generic (x86_64)
CPU: Intel i3-3220
Mobo: Gigabyte H77M-D3H
GPU: Radeon RX 480 (drivers via oibaf "graphics-drivers" ppa)

_**Thermald Query:**_
```
sudo systemctl status thermald.service
```
```

&#9679; thermald.service - Thermal Daemon Service
   Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
   Active: active (running) since Thu 2019-12-05 14:30:13 NZDT; 7h ago
 Main PID: 800 (thermald)
    Tasks: 2 (limit: 4915)
   Memory: 6.1M
   CGroup: /system.slice/thermald.service
           &#9492;&#9472;800 /usr/sbin/thermald --no-daemon --dbus-enable

Dec 05 14:30:13 sikryl systemd[1]: Started Thermal Daemon Service.
Dec 05 14:30:13 sikryl thermald[800]: [WARN]13 CPUID levels; family:model:stepping 0x6:3a:9 (6:58:9)
Dec 05 14:30:13 sikryl thermald[800]: [WARN]Polling mode is enabled: 4
Dec 05 14:30:14 sikryl thermald[800]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dec 05 14:30:14 sikryl thermald[800]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dec 05 14:30:14 sikryl thermald[800]: [WARN]sysfs open failed
Dec 05 14:30:14 sikryl thermald[800]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dec 05 14:30:14 sikryl thermald[800]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
Dec 05 14:30:14 sikryl thermald[800]: I/O warning : failed to load external entity "/etc/thermald/thermal-conf.xml"
Dec 05 14:30:14 sikryl thermald[800]: [WARN]error: could not parse file /etc/thermald/thermal-conf.xml
```

I read that the failure to load /etc/thermald/thermal-conf.xml should not be an issue.


Does anyone know how I should go about fixing this?
Thanks.

---

### Post by Doug S on 2019-12-05
There was [a similar case]("https://ubuntuforums.org/showthread.php?t=2432418"), involving the same kernel version, just the other day.
The temporary solution was to use kernel 5.3.0-19 instead.

---

### Post by xaxazak on 2019-12-06
I tried downgrading to 5.3.0-19 and it broke my graphics - it might be because I'm using oibaf video drivers, not sure.

---

### Post by bunny9000 on 2019-12-08
What? Is your computer passive cooled. If you have a good cooler & no dust in the computer it shouldn't need to throttle the cpu to stop it melting.

---

