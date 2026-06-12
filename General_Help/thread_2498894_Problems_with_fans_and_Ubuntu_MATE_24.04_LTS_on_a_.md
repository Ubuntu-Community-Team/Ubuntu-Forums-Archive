---
title: "Problems with fans and Ubuntu MATE 24.04 LTS on a Mini PC"
date: 2024-07-02
forum: General Help
---

### Post by asusg71v on 2024-07-02
[COLOR=#0C0D0E]I have an issue with the refrigeration fan of my Mini PC when I use Ubuntu MATE 24.04 LTS.[/COLOR]
[COLOR=#0C0D0E]The PC works as usual without any type of issue but I'm noticing that the fan doesn't activate even when the temperature is near 80ºC.[/COLOR]
[COLOR=#0C0D0E]I'd try activating thermald by setting up an XML in order to try to "force" the fan to wake up when the temperature hits an specific value and turn off when the temperature reaches other value. It looks like it also won't work.[/COLOR]
Here it is what I can see when I run sensors
[COLOR=#0C0D0E][FONT=-apple-system]
[FONT=arial][HTML]antonio@antonio-GN34:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +46.0°C  (high = +105.0°C, crit = +105.0°C)
Core 0:        +46.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:        +46.0°C  (high = +105.0°C, crit = +105.0°C)
Core 2:        +42.0°C  (high = +105.0°C, crit = +105.0°C)
Core 3:        +42.0°C  (high = +105.0°C, crit = +105.0°C)

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:        +42.0°C  

acpitz-acpi-0
Adapter: ACPI interface temp1:        +44.0°C [/HTML][/FONT]

[/FONT]thermal-conf.xml for thermald is set-up as the following
[/COLOR]
[HTML]antonio@antonio-GN34:~$ cat /etc/thermald/thermal-conf.xml<thermal_conf version="1">
    <thermal_zone>
        <type>coretemp</type>
        <trip_point>
            <type>active</type>
            <temperature>50000</temperature>
            <hysteresis>5000</hysteresis>
            <control type="fan" path="/sys/class/thermal/cooling_device0/cur_state" />
        </trip_point>
    </thermal_zone> </thermal_conf>[/HTML]

[COLOR=#0C0D0E][FONT=-apple-system][FONT=arial]The content of /sys/class/thermal/cooling_device0 is[/FONT][/FONT][/COLOR]
[HTML]antonio@antonio-GN34:/sys/class/thermal/cooling_device0$ ls -latotal 0
drwxr-xr-x  4 root root    0 jul  1 20:40 .
drwxr-xr-x 13 root root    0 jul  1 20:40 ..
-rw-r--r--  1 root root 4096 jul  1 20:40 cur_state
lrwxrwxrwx  1 root root    0 jul  1 20:52 device -> ../../../platform/PNP0C0B:00
-r--r--r--  1 root root 4096 jul  1 20:40 max_state
drwxr-xr-x  2 root root    0 jul  1 20:52 power
drwxr-xr-x  2 root root    0 jul  1 20:52 stats
lrwxrwxrwx  1 root root    0 jul  1 20:40 subsystem -> ../../../../class/thermal
-r--r--r--  1 root root 4096 jul  1 20:40 type 
-rw-r--r-- 1 root root 4096 jul 1 20:40 uevent[/HTML]
[COLOR=#0C0D0E][FONT=-apple-system][FONT=arial]Am I missing something or doing something wrong? I don't want the miniPC to have problems with temperature now that summer is here...[/FONT][/FONT][/COLOR]
[COLOR=#0C0D0E][FONT=-apple-system][FONT=arial]Thank you all so much in advance![/FONT][/FONT][/COLOR]

---

### Post by currentshaft on 2024-07-02
Have you checked BIOS settings? Fans usually have a "performance" mode you can set to increase RPM under load and keep the system cool.

---

### Post by asusg71v on 2024-07-02
> **currentshaft said:**
> Have you checked BIOS settings? Fans usually have a "performance" mode you can set to increase RPM under load and keep the system cool.

Hi!

I'd check BIOS settings and I only have the options to set Secure Boot and Boot Options. It's a very simple BIOS.

Thank you

---

