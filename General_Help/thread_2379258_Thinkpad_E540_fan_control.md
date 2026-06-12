---
title: "Thinkpad E540 fan control"
date: 2017-12-03
forum: General Help
---

### Post by mexp on 2017-12-03
I recently updated the bios of my Thinkpad E540, and it made some changes to the fan operation. Now it happens that the fan goes on and off pretty constantly, which is annoying when working in silent places. 

I could not find any recent instructions or guides how to enable fan control. A good solution would be to be able to keep the fan on on low speed instead of turning on and off. 

Anyone knows good resources to configure this?

I'm using Ubuntu 16.04.

---

### Post by Yellow Pasque on 2017-12-03
google thinkfan

---

### Post by mexp on 2017-12-05
Found this: [http://andrewjackson.name/blog/2016/08/07/set-up-thinkfan-on-lenovo-thinkpad-t430-ubuntu-16-04/](http://andrewjackson.name/blog/2016/08/07/set-up-thinkfan-on-lenovo-thinkpad-t430-ubuntu-16-04/)

So far I did this:

[FONT=Courier New]sudo apt-get install lm-sensors
sudo sensors-detect
sudo modprobe coretemp
sudo apt-get install thinkfan
sudo find /sys/devices -type f -name "temp*_input"
sudo gedit /etc/thinkfan.conf[/FONT]

[INDENT]hwmon /sys/devices/virtual/hwmon/hwmon0/temp1_input
tp_fan /proc/acpi/ibm/fan

(0,	0,	55)
(1,	48,	60)
(2,	50,	61)
(3,	52,	63)
(4,	56,	65)
(5,	59,	66)
(7,	63,	32767)[/INDENT]

[FONT=Courier New]sudo echo "options thinkpad_acpi fan_control=1" >> /etc/modprobe.d/thinkpad.conf[/FONT] (did not work, got permission denied, so created a file with gedit with "options thinkpad_acpi fan_control=1" on it.

Rebooted, and tried 
[FONT=Courier New]sudo thinkfan -n[/FONT]

Getting lines like this:
WARNING: You're using simple temperature limits without correction values, and your fan will only start at 55 °C. This can be dangerous for your hard drive.

sleeptime=5, tmax=53, last_tmax=53, biased_tmax=53 -> fan="level 3"
sleeptime=5, tmax=52, last_tmax=53, biased_tmax=52 -> fan="level 2"
sleeptime=2, tmax=56, last_tmax=52, biased_tmax=62 -> fan="level 3"
sleeptime=2, tmax=61, last_tmax=56, biased_tmax=68 -> fan="level 7"...

So I guess it's working. 

[FONT=Courier New]cat /proc/acpi/ibm/fan[/FONT] or sensors-command does not show any speed for fan, though, only the level.

[FONT=Courier New]echo coretemp >> /etc/modules[/FONT] also did not work, is this necessary?

---

### Post by mexp on 2017-12-05
Too early to "celebrate"... The fan does not follow /etc/thinkfan.conf parameters, but works with some other limits. I have now the thinkfan.conf as follows:

[INDENT]hwmon /sys/devices/virtual/hwmon/hwmon0/temp1_input
tp_fan /proc/acpi/ibm/fan

(0, 0, 60)
(1, 57, 63)
(2, 60, 66)
(3, 64, 68)
(4, 66, 72)
(5, 70, 74)
(7, 72, 32767)[/INDENT]

And [FONT=Courier New]sudo thinkfan -n[/FONT] shows

[FONT=Courier New]WARNING: You're using simple temperature limits without correction values, and your fan will only start at 60 °C. This can be dangerous for your hard drive.

sleeptime=5, tmax=52, last_tmax=52, biased_tmax=52 -> fan="level 0"
sleeptime=2, tmax=58, last_tmax=53, biased_tmax=65 -> fan="level 2"
sleeptime=5, tmax=53, last_tmax=58, biased_tmax=53 -> fan="level 0"[/FONT]

[FONT=Courier New]sensors[/FONT] show this:

[FONT=Courier New]coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +52.0°C  (high = +84.0°C, crit = +100.0°C)
Core 0:        +51.0°C  (high = +84.0°C, crit = +100.0°C)
Core 1:        +52.0°C  (high = +84.0°C, crit = +100.0°C)

acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +127.0°C)[/FONT]

And the fan only stops at 50 degrees.

Any ideas how to get it running correctly?

---

### Post by gordintoronto on 2017-12-05
Your Thinkpad is running pretty hot. It might be worthwhile to clean the CPU fan and vacuum the inside.

Sorry, I can't answer your question.

---

### Post by mexp on 2017-12-06
It's just cleaned, wasn't too dusty or anything :) 

Even before this tinkering with the fan, the temperature got up to 55 degrees before the fan turned on. Before the bios update the normal operating temperature was around 45 degrees, with the fan on all the time.

---

