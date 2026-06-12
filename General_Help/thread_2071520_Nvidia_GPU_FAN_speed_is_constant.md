---
title: "Nvidia GPU FAN speed is constant"
date: 2012-10-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-10-15
I have a [GTX 550 Ti]("http://www.asus.com/Graphics_Cards/NVIDIA_Series/ENGTX550_Ti_DCDI1GD5/")
i was working on a script to monitor the GPU usage when i noticed something scary, my fan speed stays at 30% regardless of the temperature, this happens on both 12.04 and 10.04 (all i checked)
both are running nvidia 304.51

is anyone able to see if there fan speed changes, i am hoping this is a reporting bug in nvidia's driver and that the fan is actually spinning faster at 50C than 30C

```
#!/bin/bash
GPU=`nvidia-smi | head -9 | tail -1 | awk '{print $2" "$3" "$9" "$10" "$12}' | sed 's/[^0-9 ]//g'`
FAN=`echo $GPU | awk '{print $1"%"}'`
DEG=`echo $GPU | awk '{print $2"°C"}'`
USE=`echo $GPU | awk '{print $3"%"}'`
MEM=`echo $GPU | awk '{print int($4/$5*100)"%"}'`
if [ "$1" == "gpu" ];then
	echo "<bar>$USE</bar>"
	echo "<tool>Usage: $USE"
	echo "Memory: $MEM</tool>"
elif [ "$1" == "mem" ];then
	echo "<bar>$MEM</bar>"
	echo "<tool>Memory: $MEM"
	echo "Usage: $USE</tool>"
else
	echo "Fan:	$FAN"
	echo "Temp:	$DEG"
	echo "Usage:	$USE"
	echo "Memory:	$MEM"
fi
```

---

### Post by essexboyracer on 2012-11-10
Nvidia 9700M GT, 2.53 core duo, asus G71v. Xubuntu 12.04, from xorg.conf # nvidia-xconfig:  version 295.40  (buildmeister@swio-display-x86-rhel47-04.nvidia.com)  Thu Apr  5 22:33:07 PDT 2012

```
oliver@oliver-G71V:~$ ./fan.sh
Fan:	59%
Temp:	23°C
Usage:	%
Memory:	-nan%
 
```

---

### Post by rai4shu2 on 2012-11-10
Have you tried 304.64? That might include a fix for that problem.

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by pqwoerituytrueiwoq on 2012-11-10
no, been on 310.14 and many stable version before that

relevant thread? maybe these should be merged...
[http://ubuntuforums.org/showthread.php?t=2079826](http://ubuntuforums.org/showthread.php?t=2079826)

---

### Post by essexboyracer on 2012-11-11
So now I am on Xubuntu 12.10, 3.5.0-18-generic. Is this the kernel overheating issue? using nvidia driver 304.43. I have no temperature setting in AMI BIOS. Am considering dropping back to a prior kernel before the overheating bug to see if that works - if that doesn't perhaps strip the laptop and clean.

```
oliver@oliver-G71V:~$ ./fan.sh
Fan:	64%
Temp:	23°C
Usage:	117%
Memory:	inf%
oliver@oliver-G71V:~$ 

```

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +52.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +47.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +50.0°C  (high = +105.0°C, crit = +105.0°C)

```

---

### Post by essexboyracer on 2012-11-11
In your script the Fan output is actually the temperature, compared to NVIDIA X Server Settings > GPU0 > Thermal Settings

Now on 304.64

```
oliver@oliver-G71V:~$ ./fan.sh
Fan:	66%
Temp:	22°C
Usage:	111%
Memory:	inf%
```


```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +54.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +49.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +51.0°C  (high = +105.0°C, crit = +105.0°C)
```

---

### Post by essexboyracer on 2012-11-11
So,opened the case. I didnt have any air to blow through, so took moistened cotton buds to the fins, which were pretty fluffy. For my particular model (Asus G71v) there are a few youtube mods (for the G50 - 15" model) that improve the airflow through the laptop. I still think its the kernel power regression bug though...

```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +47.0°C  (crit = +110.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +105.0°C, crit = +105.0°C)
Core 1:       +45.0°C  (high = +105.0°C, crit = +105.0°C)

oliver@oliver-G71V:~$ ./fan.sh
Fan:	60%
Temp:	13°C
Usage:	65%
Memory:	inf%

```

---

### Post by pqwoerituytrueiwoq on 2012-11-11
> **essexboyracer said:**
> So,opened the case. I didnt have any air to blow through, so took moistened cotton buds to the fins, which were pretty fluffy. For my particular model (Asus G71v) there are a few youtube mods (for the G50 - 15" model) that improve the airflow through the laptop. I still think its the kernel power regression bug though...
assuming you are own topic, my fan speed does not change on the 2.6 kernel for the 3.6.3 kernel
temps stay below 56C and idle under 30C

---

### Post by rai4shu2 on 2012-11-11
Have you double-checked with nvidia-settings (in the Thermal Settings dialog)? You might be running into an issue with nvidia-smi.

---

### Post by efflandt on 2012-11-11
Fan speed does not increase beyond 30% until the GPU gets above 62 degrees C, so no difference at 50 vs. 30 degrees C is not hot enough to even be an issue (green zone in NVIDIA X Server Settings).  The only way I can get it hot enough to increase fan speed is to run minecraft flat out on Fast instead of Balanced.  Is there some reason you feel that you need most recent drivers.  The default 295.40 version in 64-bit 12.04 still works fine for GTX 550 Ti (which is not a really new model).

```
+------------------------------------------------------+                       
| NVIDIA-SMI 3.295.40   Driver Version: 295.40         |                       
|-------------------------------+----------------------+----------------------+
| Nb.  Name                     | Bus Id        Disp.  | Volatile ECC SB / DB |
| Fan   Temp   Power Usage /Cap | Memory Usage         | GPU Util. Compute M. |
|===============================+======================+======================|
| 0.  GeForce GTX 550 Ti        | 0000:01:00.0  N/A    |       N/A        N/A |
|  33%   64 C  N/A   N/A /  N/A |  56%  577MB / 1023MB |  N/A      Default    |
|-------------------------------+----------------------+----------------------|
| Compute processes:                                               GPU Memory |
|  GPU  PID     Process name                                       Usage      |
|=============================================================================|
|  0.           Not Supported                                                 |
+-----------------------------------------------------------------------------+
```

---

### Post by pqwoerituytrueiwoq on 2012-11-11
i either use xorg edgers or xswat, currently using 310.14 from xorg edgers
but now i know why the fan speed never goes up for me it is cause the HSF on the GPU is just that good, is there a way to make start increasing  at say 45C instead of 60C

---

