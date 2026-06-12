---
title: "Daemon thermald is only for CPU Intel ?"
date: 2023-06-27
forum: General Help
---

### Post by aug7744 on 2023-06-27
Hello.
Thanks for reading my topic.
The module thermald is only for Intel CPUs or works for AMD too ?
I see if removing intel firmware microcode package is removed thermald too.
Have an nice week.

---

### Post by MAFoElffen on 2023-06-28
No. Do some more reading...

As per the Ubuntu Manpage for thermald, it is not a kernel module. It is a daemon, and is installed and enable whether you have Intel or AMD as a CPU.
RE: [https://manpages.ubuntu.com/manpages/xenial/man8/thermald.8.html](https://manpages.ubuntu.com/manpages/xenial/man8/thermald.8.html)

See this output here? This is Ubuntu 22.04.2 LTS on an AMD CPU system:
```

mafoelffen@opti-ubuntu:~$ sudo systemctl status thermald | grep .
&#9675; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Thu 2023-06-08 01:44:54 PDT; 2 weeks 6 days ago
   Main PID: 1437 (code=exited, status=0/SUCCESS)
        CPU: 26ms
Jun 08 01:44:54 opti-ubuntu systemd[1]: Starting Thermal Daemon Service...
Jun 08 01:44:54 opti-ubuntu systemd[1]: Started Thermal Daemon Service.
Jun 08 01:44:54 opti-ubuntu thermald[1437]: NO RAPL sysfs present
Jun 08 01:44:54 opti-ubuntu thermald[1437]: Unsupported cpu model or platform
Jun 08 01:44:54 opti-ubuntu systemd[1]: thermald.service: Deactivated successfully.

mafoelffen@opti-ubuntu:~$ ls /sys/class/thermal
cooling_device0   cooling_device12  cooling_device2  cooling_device6
cooling_device1   cooling_device13  cooling_device3  cooling_device7
cooling_device10  cooling_device14  cooling_device4  cooling_device8
cooling_device11  cooling_device15  cooling_device5  cooling_device9

mafoelffen@opti-ubuntu:~$ grep 'name' /proc/cpuinfo | head -n 1
model name    : AMD Opteron(tm) Processor 6386 SE

```
On an AMD CPU system: It is enabled, and during the boot process, sees that there are no Intel Thermal sensors in the sysfs of /sys/class/thermal/, so it shuts itself off, because it has nothing to do. It is present on systems with an AMD CPU.

Here is the difference of those on an Intel CPU system:
```

mafoelffen@Mikes-B460M:~$ sudo systemctl status thermald | grep .
&#9679; thermald.service - Thermal Daemon Service
     Loaded: loaded (/lib/systemd/system/thermald.service; enabled; vendor preset: enabled)
     Active: active (running) since Tue 2023-06-20 09:22:22 PDT; 1 week 1 day ago
   Main PID: 3952 (thermald)
      Tasks: 2 (limit: 154235)
     Memory: 2.7M
     CGroup: /system.slice/thermald.service
             &#9492;&#9472;3952 /usr/sbin/thermald --systemd --dbus-enable --adaptive
Jun 20 09:22:22 Mikes-B460M systemd[1]: Started Thermal Daemon Service.
Jun 20 09:22:22 Mikes-B460M thermald[3952]: 22 CPUID levels; family:model:stepping 0x6:a5:5 (6:165:5)
Jun 20 09:22:22 Mikes-B460M thermald[3952]: 22 CPUID levels; family:model:stepping 0x6:a5:5 (6:165:5)
Jun 20 09:22:22 Mikes-B460M thermald[3952]: sensor id 8 : No temp sysfs for reading raw temp
Jun 20 09:22:22 Mikes-B460M thermald[3952]: sensor id 8 : No temp sysfs for reading raw temp
Jun 20 09:22:22 Mikes-B460M thermald[3952]: sensor id 8 : No temp sysfs for reading raw temp
Jun 20 09:22:22 Mikes-B460M thermald[3952]: Config file /etc/thermald/thermal-conf.xml does not exist
Jun 20 09:22:22 Mikes-B460M thermald[3952]: Config file /etc/thermald/thermal-conf.xml does not exist
Jun 20 09:22:22 Mikes-B460M thermald[3952]: Config file /etc/thermald/thermal-conf.xml does not exist
Jun 20 09:22:22 Mikes-B460M thermald[3952]: Polling mode is enabled: 4

mafoelffen@Mikes-B460M:~$ ls /sys/class/thermal
cooling_device0   cooling_device16  cooling_device23  cooling_device7
cooling_device1   cooling_device17  cooling_device24  cooling_device8
cooling_device10  cooling_device18  cooling_device25  cooling_device9
cooling_device11  cooling_device19  cooling_device26  thermal_zone0
cooling_device12  cooling_device2   cooling_device3   thermal_zone1
cooling_device13  cooling_device20  cooling_device4   thermal_zone2
cooling_device14  cooling_device21  cooling_device5   thermal_zone3
cooling_device15  cooling_device22  cooling_device6   thermal_zone4

mafoelffen@Mikes-B460M:~$ grep 'name' /proc/cpuinfo | head -n 1
model name    : Intel(R) Core(TM) i9-10900 CPU @ 2.80GHz

```
So the question might rather be reworded towards the "what" of what you are trying to do or see...

---

### Post by aug7744 on 2023-06-29
Thanks for your reply.
I had accessed an page with information related only for Intel so doing doubt.
Topic title fixed.
Have an nice day.

---

