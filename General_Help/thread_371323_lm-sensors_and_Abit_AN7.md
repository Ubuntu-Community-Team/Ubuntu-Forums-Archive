---
title: "lm-sensors and Abit AN7"
date: 2007-02-26
forum: General Help
---

### Post by pbt1957 on 2007-02-26
Has **anyone** gotten lm-sensors working on an Abit AN7, Winbond chip W83627HF, Amd 2800+(Athlon or Sempron, not sure)  using Dapper 6.06, kernel 2.6.15-28-k7? I have gone over all the following, so far without complete success.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)
[http://www.ubuntuforums.org/showthread.php?t=2780](http://www.ubuntuforums.org/showthread.php?t=2780)

So far I have only achieved 3 voltage readings going thru the above 2 links.

[http://www.lm-sensors.org/wiki/Configurations/Abit/AN7](http://www.lm-sensors.org/wiki/Configurations/Abit/AN7)

The last link shows-

# lm_sensors configuration file for the Abit AN7 motherboard
# Note the driver MUST be loaded with the following params:
# bank1_types=1,1,0,0,0,0,0,2,0,0,0,0,2,0,0,1 fan_sensors=5

chip "abituguru-*"

Where do I put the 'params'? How find if I have 'abituguru' already installed somewhere on my box? Somewhere I read it would be used in place of 'w83627hf' in etc/modules, Abit has aparentley re-programmed the Winbond.

[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

This page says I need kernel 2.6.18. How do I get at least that one for Dapper?

---

### Post by Icarosaurus on 2007-03-01
Got it work!
I own an Abit AN7 with an Athlon 2500+ and I'm running Feisty (2.6.20-9-generic).
I don't know if you can easily update your kernel...search in the forum...or update to Edgy :).
Thanks to your links and the lm-sensors thread in this forum I made it work in a hurry :)
So...this is a little HOWTO (a lot of it is a copy of [the original lm-sensors  thread]("http://www.ubuntuforums.org/showthread.php?t=2780")).

**1.** Install lm-sensors using apt-get or the Synaptic GUI.

```
sudo apt-get install lm-sensors
```

**2.** make a mkdev.sh script:

*a.* Copy the script file below to a text editor and save it to a file named mkdev.sh.

```
#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
#end of file
```

*b.* Make the file executable:

```
chmod 755 mkdev.sh
```

*c.* Run mkdev.sh from the current directory

```
sudo ./mkdev.sh
```

**3.** You don't need to run sensors-detect: it fails to detect the right sensors.
In fact, we don't need W83627HF at all.

**4.** Directly modify **/etc/modules**

```
sudo gedit /etc/modules
```

This is my /etc/modules for example:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp

# Modules needed for lm-sensors
eeprom
abituguru bank1_types=1,1,0,0,0,0,0,2,0,0,0,0,2,0,0,1 fan_sensors=5

```

**5.** you should have "alias char-major-89-* i2c_dev" in /etc/modprobe.d/aliases. If you don't have just modify or create "/etc/modprobe.d/local" and add the line "alias char-major-89 i2c-dev".

**6.** create your own sensors.conf and take a backup of the old one:

```
sudo mv /etc/sensors.conf /etc/sensors.conf.old
sudo gedit /etc/sensors.conf

```

Paste the code you found in [http://www.lm-sensors.org/wiki/Configurations/Abit/AN7]("http://www.lm-sensors.org/wiki/Configurations/Abit/AN7")

```
# lm_sensors configuration file for the Abit AN7 motherboard
# 2006-06-24, Hans de Goede <j.w.r.degoede@hhs.nl>
# Comments welcome!
# Note the driver MUST be loaded with the following params:
# bank1_types=1,1,0,0,0,0,0,2,0,0,0,0,2,0,0,1 fan_sensors=5

chip "abituguru-*"


### Voltages


   label in0 "CPU Core Voltage"

   label in1 "DDR Voltage"

   label in2 "DDR VTT Voltage"

   label in3 "ATX +12V"
   compute in3 @*4.153 , @/4.153

   # I believe this is FSB VTT, in some Abit files its called GMCHVTT, below is the BIOS name
   label in4 "AUXC Voltage"  

   label in5 "NB Core Voltage"

   label in6 "AGP VDDQ Voltage"

   label in7 "ATX +5V Voltage"
   compute in7 @*1.788 , @/1.788

   label in8 "ATX +3.3V Voltage"
   compute in8 @*1.248 , @/1.248

   label in9 "Standby Voltage (+5V)"   
   compute in9 @*1.788 , @/1.788

   label in10 "3VDUAL Voltage"
   compute in10 @*1.248 , @/1.248


### Temperatures


   label temp1 "CPU Temperature"

   label temp2 "System Temperature"

   label temp3 "PWM Temperature"

   ignore temp4

   ignore temp5

   ignore temp6

   ignore temp7


### Fans


   label fan1 "CPU FAN Speed"

   label fan2 "NB FAN Speed"  

   label fan3 "SYS FAN Speed"

   label fan4 "FAN4"

   label fan5 "FAN5"

   ignore fan6

```


**7.** Reset your machine or try loading the modules manually:

```
sudo modprobe eeprom
sudo modprobe abituguru bank1_types=1,1,0,0,0,0,0,2,0,0,0,0,2,0,0,1 fan_sensors=5
```

**8.** by typing: ```
sensors
```
...you should see something like this:

```
abituguru-isa-00e0
Adapter: ISA adapter
CPU Core Voltage:       +1.70 V (min  +0.00 V, max  +3.49 V)
DDR Voltage:            +2.71 V (min  +0.00 V, max  +3.49 V)
DDR VTT Voltage:        +1.36 V (min  +0.00 V, max  +3.49 V)
ATX +12V:              +12.06 V (min  +0.00 V, max +14.51 V)
AUXC Voltage:           +1.66 V (min  +0.00 V, max  +3.49 V)
NB Core Voltage:        +1.66 V (min  +0.00 V, max  +3.49 V)
AGP VDDQ Voltage:       +1.62 V (min  +0.00 V, max  +3.49 V)
ATX +5V Voltage:        +5.19 V (min  +0.00 V, max  +6.25 V)
ATX +3.3V Voltage:      +3.35 V (min  +0.00 V, max  +4.36 V)
Standby Voltage (+5V):  +5.19 V (min  +0.00 V, max  +6.25 V)
3VDUAL Voltage:         +3.32 V (min  +0.00 V, max  +4.36 V)
CPU Temperature:          +31°C  (high =   +75°C, crit =  +214°C)  
System Temperature:       +26°C  (high =  +255°C, crit =  +255°C)  
PWM Temperature:          +30°C  (high =  +255°C, crit =  +255°C)  
CPU FAN Speed:         4080 RPM (min    0 RPM)               
NB FAN Speed:          4380 RPM (min   60 RPM)               
SYS FAN Speed:         2340 RPM (min  120 RPM)               
FAN4:                  2340 RPM (min  180 RPM)               
FAN5:                     0 RPM (min  240 RPM)               

```

**9.** you should tweak sensors.conf to get the right limits and readings... I'll do this in future... making it work is enough for me :)

Let me know if it works! Greetings!

---

### Post by ffxr on 2007-03-01
i have been having similar issues with my sg95 board.. do you know how i find out if my board has 'uguru'? its not mentioned in my manual & i cant find anything on the abit site...?


its fairly easy to complie your own kernel by the way.. 
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Icarosaurus on 2007-03-01
I don't know if your motherboard has uguru.
I checked the website and yes...there aren't useful informations on the Abit site and in the manual...
I'd try:
```
sudo modprobe abituguru
dmesg | grep uguru
```
and check the output...
you should see something like this at the end of the output:
```

[   41.734831] abituguru: found Abit uGuru
```

Of course, you can compile your own kernel too :)

---

### Post by mrcanard on 2007-05-29
> **Icarosaurus said:**
> Got it work!
(large snip)
Let me know if it works! Greetings!

Works great!
Thank you very much!

Best Regards,

---

### Post by Icarosaurus on 2007-05-30
Glad to know!
Personally I use the sensors applet on the panel for monitoring cpu temperature....

---

### Post by mrcanard on 2007-05-31
> **Icarosaurus said:**
> Glad to know!
Personally I use the sensors applet on the panel for monitoring cpu temperature....

The sensor applet is non-obtrusive and easy to see.

I have the radiator fan sensor lead plugged into the cpu fan header. Seems to read right.

The NB fan shows about 5k rmp, I thought it was a 2.5k fan? I'll check the specs this weekend.

The cpu temp reads about 10 degrees C over ambient and about 4 degrees lower than the AN7 w/ a comparable  air cooled cpu box running W2k. Both at normal load.

The PWM reads about 10 degrees over the cpu temp. This may be normal or due to reduced airflow. If I can find the PWM temp in SpeedFan on the W2k box I'll compare. If not I'll point a fan at the PWM and see if it changes.  This reading is way in spec and is really nothing to worry about. I'm wondering what yours reads?

Regards,

---

### Post by Icarosaurus on 2007-06-03
Hello, this is what I get:
```

abituguru-isa-00e0
Adapter: ISA adapter
CPU Core Voltage:       +1.69 V (min  +0.00 V, max  +3.49 V)
DDR Voltage:            +2.71 V (min  +0.00 V, max  +3.49 V)
DDR VTT Voltage:        +1.38 V (min  +0.00 V, max  +3.49 V)
ATX +12V:              +12.06 V (min  +0.00 V, max +14.51 V)
AUXC Voltage:           +1.66 V (min  +0.00 V, max  +3.49 V)
NB Core Voltage:        +1.66 V (min  +0.00 V, max  +3.49 V)
AGP VDDQ Voltage:       +1.62 V (min  +0.00 V, max  +3.49 V)
ATX +5V Voltage:        +5.19 V (min  +0.00 V, max  +6.25 V)
ATX +3.3V Voltage:      +3.35 V (min  +0.00 V, max  +4.36 V)
Standby Voltage (+5V):  +5.17 V (min  +0.00 V, max  +6.25 V)
3VDUAL Voltage:         +3.32 V (min  +0.00 V, max  +4.36 V)
**CPU Temperature:          +48°C**  (high =   +75°C, crit =  +214°C)  
**System Temperature:       +36°C**  (high =  +255°C, crit =  +255°C)  
**PWM Temperature:          +41°C**  (high =  +255°C, crit =  +255°C)  
CPU FAN Speed:         4020 RPM (min    0 RPM)               
**NB FAN Speed:          4500 RPM** (min   60 RPM)               
SYS FAN Speed:         2460 RPM (min  120 RPM)               
FAN4:                  2340 RPM (min  180 RPM)               
FAN5:                     0 RPM (min  240 RPM)
```

Outer temperature is about 17°C, so maybe Room temperature is about 20°C.

All Temperature readings seems normal to me...I'm keeping the case open.
NB fan showed about 4000RPM under win too...

So I think sensors output is correct.

Regards.

---

### Post by fjf on 2007-08-16
I tried this with my abit ip35 pro that has the same winbond chip.  All I get after 'sensors' is:

No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
After 

sudo modprobe abituguru
dmesg | grep uguru 

I get :  [   14.730211] abituguru: timeout exceeded waiting for ready state

Any ideas?.

---

### Post by fjf on 2007-08-17
bump

---

### Post by Icarosaurus on 2007-08-27
no ideas...
are you sure you motherboard uses uguru?

---

### Post by fjf on 2007-08-29
Yes, it does.

---

### Post by Icarosaurus on 2007-09-01
Look here:
[http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices")
maybe we're talking about uguru revison 3..
it says the driver is abituguru3...
I'd try 
> sudo modprobe abituguru3
sensors

and see what it happens

---

### Post by fjf on 2007-09-06
FATAL: Module abituguru3 not found

How do I get this module?.

---

### Post by Icarosaurus on 2007-09-06
If you go there again:
[http://www.lm-sensors.org/wiki/Devices]("http://www.lm-sensors.org/wiki/Devices")
You'll find that abituguru3 is supported since Kernel 2.6.23.
Well... I have 2.6.20
Check with:
```

uname -r

```
I think this kernel will be in Gutsy (it has 2.6.22 now). Your motherboard is really new... so you have to wait a bit if you want to find it as a package to use on the fly in Ubuntu ;)
P.S.: you can still compile a 2.6.23 kernel by yourself....

---

### Post by fjf on 2007-09-07
2.6.22-9-generic

I upgraded to the Gutsy kernel, but it seems it is not enough...I'll wait until 23 is available.  Thanks for your help!.

---

### Post by fjf on 2007-09-09
Well, I still dont believe it, but following the master kernel thread I was able to compile (using the script) the kernel 2.6.23-rc5.  It is not totally stable, but seems to work.  Usinf your conf files and modprobing eeprom and abituguru3 all I get is:

abituguru3-isa-00e0
Adapter: ISA adapter

But not values at all. I guess I'll have to wait until someone posts the conf files for my mobo.  Any suggestions I might try?.

---

### Post by mrcanard on 2007-10-24
> **Icarosaurus said:**
> Got it work!
Let me know if it works! Greetings!

I did a clean install to 7.10 and your How To worked for me.

The AN9 will have to wait awhile before it's migrated to 7.10 and an attempt  is made to make the senors work. Ubuntu64 has been a little trippy.

Thanks Again,

---

