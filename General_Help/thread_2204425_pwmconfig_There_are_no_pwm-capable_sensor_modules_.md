---
title: "pwmconfig: There are no pwm-capable sensor modules installed"
date: 2014-02-08
forum: General Help
---

### Post by Ian_Francis on 2014-02-08
Hi guys,

I hope you can help. I'm trying to control my case fan using fancontrol. My motherboard does have "Fan xpert" on the CPU & CHASSIS1 Fans but I'm trying to keep my hard drives cool and, I'm guessing, this feature adjusts the fan speeds based on the motherboard or CPU temps which is no good. 

Anyway, I've run sensors-detect and it's run through without issue and running "sensors" results in the following output:

```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +36.0°C  (high = +78.0°C, crit = +100.0°C)
Core 1:       +36.0°C  (high = +78.0°C, crit = +100.0°C)


atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.08 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:       +3.26 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +4.99 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.21 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:       897 RPM  (min =  600 RPM)
CHASSIS1 FAN Speed:    0 RPM  (min =  600 RPM)
POWER FAN Speed:       0 RPM  (min =  600 RPM)
CPU Temperature:     +27.5°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +42.0°C  (high = +45.0°C, crit = +95.0°C)

```
Note: I've currently removed the fans from the CHASSIS1 & POWER FAN connectors for the time being until I've got this issue solved as they were causing the fans to run too slowly and my hard drives were getting too hot.

I've installed fancontrol and when I run pwmconfig it gives me "There are no pwm-capable sensor modules installed". This is the content of my /sys/class/hwmon/hwmon1 folder. fan3_* is my CHASSIS Fan. I note all files are read-only for root.

```
lrwxrwxrwx 1 root root    0 Feb  7 07:50 device -> ../../../ATK0110:00
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan1_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan1_label
-r--r--r-- 1 root root 4096 Feb  8 15:40 fan1_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan1_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan2_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan2_label
-r--r--r-- 1 root root 4096 Feb  8 15:40 fan2_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan2_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan3_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan3_label
-r--r--r-- 1 root root 4096 Feb  8 15:40 fan3_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 fan3_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 in0_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 in0_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 in0_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 in0_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 in1_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 in1_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 in1_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 in1_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 in2_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 in2_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 in2_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 in2_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 in3_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 in3_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 in3_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 in3_min
-r--r--r-- 1 root root 4096 Feb  7 07:50 name
drwxr-xr-x 2 root root    0 Feb  8 10:35 power
lrwxrwxrwx 1 root root    0 Feb  8 15:40 subsystem -> ../../../../../../../../class/hwmon
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp1_crit
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp1_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp1_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp1_max
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp2_crit
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp2_input
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp2_label
-r--r--r-- 1 root root 4096 Feb  7 07:50 temp2_max
-rw-r--r-- 1 root root 4096 Feb  8 15:40 uevent

```

I'm running Ubuntu 12.04LTS 64bit and my motherboard in an ASUS P5Q-EM.

Can someone give me some pointers on how to get pwmconfig to work properly?

Many thanks,

Ian.

---

### Post by Ian_Francis on 2014-02-13
Hi guys,

Is no one able to help me? :(

Ian.

---

### Post by Yellow Pasque on 2014-02-14
You probably have to turn off Qfan/Fanxpert in the BIOS if you want to use pwmconfig/fancontrol scripts. Hopefully, that will allow the chassis fan to run at normal speed. Note that mobo makers have a maddening habit of not spending the extra $0.25 to implement PWM circuitry on non-CPU headers, so don't assume that all your fan headers are capable of it. 

Your other option is to get a fan with a Molex connector and plug it straight into the PSU.

---

### Post by Ian_Francis on 2014-02-14
Hi there and thanks for the reply. 
 
I've already tried disabling the options in the BIOS but still no joy. The CPU fan has a 4 pin header and the chassis and case fan headers are 3 pin. According to the manual "Only the CPU Fan and the Chassis Fan connectors support the ASUS Fan Xpert feature" which I take to mean the speed of both is controllable via Ubuntu. 

I'm not very proficient at reading code but it looks like the pwmconfig script is merely looking for files prefixed "pwm" of which I have none. Furthermore, the files are read-only which makes me think "something" is not working properly. Whether it's the process which creates those files or not I do not know.
 
Currently the case fans are connected via molex to the PSU. The trouble is they run at full speed and are noisy. I only want them to run at full speed when they need to ;)

Ian.

---

### Post by Yellow Pasque on 2014-02-14
> The trouble is they run at full speed and are noisy. I only want them to run at full speed when they need to
Then you should probably get better fans (I use Yate Loon 120mm's) and/or a fan controller. From some quick Googling, people with your mobo complain about the same issue where the fan headers are linked together and can't be controlled independently (and they're using SpeedFan under Windows).

I personally think you're SOL as far as using PWM, but for your sake, I hope I'm wrong. :\

---

### Post by Ian_Francis on 2014-02-14
I've got Noctua NF-S12As which are pretty quiet fans but at full speed they still make my server pretty loud. With the fans connected to the motherboard you can barely hear them and when the hard drives are idle everything is fine. BUT when I stress the drives (there are 10 in there) the fans can't keep them cool and the temps go from 27-28°C to 40+°C.  With the fans on full speed (connected directly to the PSU) the drives barely reach 30-32°C under the same level of usage.
 
Is there a fan controller out there which can monitor the temp of each drive and adjust the fans accordingly? If not, then it looks like I'll need to change my motherboard. Are there any which are guaranteed to work with fancontrol?

Ian.

---

### Post by Yellow Pasque on 2014-02-14
> the temps go from 27-28C to 40C+

You do know that desktop drives are spec'd to run fine until 60C or higher, right?

You do know that young drives (<= 2 years old) actually fail at higher rates when running at colder temps, right? [http://storagemojo.com/2007/02/19/googles-disk-failure-experience/](http://storagemojo.com/2007/02/19/googles-disk-failure-experience/)

If the drives idle between 30-40C and don't top 50-55C under extended heavy load, then you're good to go. If you get a fan controller to slow down the Noctua a bit, you shouldn't have an issue maintaining those temps, unless you have a bunch of drives that pull a lot of power and are packed together enough to hinder airflow.

---

### Post by Ian_Francis on 2014-02-18
Thanks for that, very interesting. ;)

Based on my own experiences tho, namely 5 drives which started failing within a few weeks of each other following a fan failure I'd still prefer to get fancontrol working. Was it a total coincidence and nothing to do with heat? Quite possibly. Would I like to repeat the exercise with more drives and data? Nope! :lolflag:

Ian.

---

