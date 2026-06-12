---
title: "How do I get live CPU and GPU Fan speed?"
date: 2023-03-07
forum: General Help
---

### Post by ricciolino on 2023-03-07
I post this new thread here as I am not able to find any functional solution to the the object question.

Details of my configuration:
- OS: Ubuntu 22.04 LTS
- Kernel version: Linux 5.19.0-35-generic (x86_64)
- MB: MAG Z690 TOMAHAWK WIFI DDR4 (MS-7D32)

I have installed lm-sensors, psensor, hardinfo. I have tried to auto-detect sensors though the "sensors" package.
I am able to see GPU Fans speed using the psensor GUI but I am not able to find any method to check my CPU Fans speed.

Can anyone help me to have more clear how to monitor fan speed in live mode?
There must be a way to get this data with some simple command-line tool.

Thanks in advance for your help.

---

### Post by coffeecat on 2023-03-07
*Thread moved to **General Help** sub-forum.*

---

### Post by TheFu on 2023-03-07
Different chipsets have different support levels.  Often, there are kernel patches or kernel modules for newer chipsets.  Sometimes, the support just isn't easily available.  For a few years, Ryzen CPU sensor support didn't exist.  I think the 6.1.x kernel will add some level of sensor support for Ryzen.  I don't keep up with Intel stuff.  Usually, standard chipsets have support fairly quickly.

You'll need to look up the exact chipset used on your board - version and revision - then look for code that provides sensor support for it.

>  There must be a way to get this data with some simple command-line tool.
Not always, I'm sorry to say.

---

### Post by hakerdefo2 on 2023-03-07
```
sudo apt-get install lm-sensors
```
```
sudo sensors-detect
```
press the **Enter** key to all questions. After this has finished, reboot the computer.
After reboot, open terminal and run,
```
sensors
```
command to get the information. You can use,
```
sensors | grep -i fan
```
to filter out the fan info. You can also use it with the **watch **command to get the continuously updated info,
```
 watch -n1 -d 'sensors | grep fan'
```
If this doesn't work, please post the output of,
```
cat /etc/sensors3.conf
```

Good luck.

---

### Post by ricciolino on 2023-03-07
Ok , I understand.
Well, actually I forgot to mention that my CPU is the **Intel (R) 13th Gen Core(TM) i7-13700K**.

---

### Post by ricciolino on 2023-03-07
> **TheFu said:**
> Different chipsets have different support levels.   Often, there are kernel patches or kernel modules for newer chipsets.   Sometimes, the support just isn't easily available.  For a few years,  Ryzen CPU sensor support didn't exist.  I think the 6.1.x kernel will  add some level of sensor support for Ryzen.  I don't keep up with Intel  stuff.  Usually, standard chipsets have support fairly quickly.

You'll need to look up the exact chipset used on your board - version  and revision - then look for code that provides sensor support for it.


Not always, I'm sorry to say.

Ok , I understand.
Well, actually I forgot to mention that my CPU is the **Intel (R) 13th Gen Core(TM) i7-13700K**.

---

### Post by ricciolino on 2023-03-07
> **hakerdefo2 said:**
> ```
sudo apt-get install lm-sensors
```
```
sudo sensors-detect
```
press the **Enter** key to all questions. After this has finished, reboot the computer.
After reboot, open terminal and run,
```
sensors
```
command to get the information. You can use,
```
sensors | grep -i fan
```
to filter out the fan info. You can also use it with the **watch **command to get the continuously updated info,
```
 watch -n1 -d 'sensors | grep fan'
```
If this doesn't work, please post the output of,
```
cat /etc/sensors3.conf
```

Good luck.

I did all the steps, but I have no "Fans" items involved in the "sensors" output.

Here is the output of the "sensors" command:

```

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +32.0°C  (high = +80.0°C, crit = +100.0°C)
Core 0:        +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 4:        +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 8:        +26.0°C  (high = +80.0°C, crit = +100.0°C)
Core 12:       +29.0°C  (high = +80.0°C, crit = +100.0°C)
Core 16:       +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 20:       +28.0°C  (high = +80.0°C, crit = +100.0°C)
Core 24:       +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 28:       +27.0°C  (high = +80.0°C, crit = +100.0°C)
Core 32:       +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 33:       +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 34:       +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 35:       +30.0°C  (high = +80.0°C, crit = +100.0°C)
Core 36:       +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 37:       +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 38:       +31.0°C  (high = +80.0°C, crit = +100.0°C)
Core 39:       +31.0°C  (high = +80.0°C, crit = +100.0°C)

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +27.8°C  (crit = +105.0°C)

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1:            N/A  

nvme-pci-0200
Adapter: PCI adapter
Composite:    +30.9°C  (low  = -20.1°C, high = +89.8°C)
                       (crit = +94.8°C)


```

And here is the content of the /etc/sensors3.conf file:

```

# libsensors configuration file
# -----------------------------
#
# This default configuration file only includes statements which do not
# differ from one mainboard to the next. Only label, compute and set
# statements for internal voltage and temperature sensors are included.
#
# In general, local changes should not be added to this file, but rather
# placed in custom configuration files located in /etc/sensors.d. This
# approach makes further updates much easier.
#
# Such custom configuration files for specific mainboards can be found in
# "configs" directory of lm-sensors package.
#
# Please contribute back a configuration of your board so other users with
# the same hardware won't need to recreate it again and again.

chip "lm78-*" "lm79-*" "lm80-*" "lm96080-*"

    label temp1 "M/B Temp"


chip "w83792d-*"

    label in0 "VcoreA"
    label in1 "VcoreB"
    label in6 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    set in6_min  5.0 * 0.90
    set in6_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.0 * 1.10


chip "w83793-*"

    label in0 "VcoreA"
    label in1 "VcoreB"
    label in7 "+5V"
    label in8 "5VSB"
    label in9 "Vbat"

    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  5.0 * 0.90
    set in8_max  5.0 * 1.10
    set in9_min  3.0 * 0.90
    set in9_max  3.0 * 1.10


chip "w83795g-*" "w83795adg-*"

    label in12 "+3.3V"
    label in13 "3VSB"
    label in14 "Vbat"

    set in12_min  3.3 * 0.90
    set in12_max  3.3 * 1.10
    set in13_min  3.3 * 0.90
    set in13_max  3.3 * 1.10
    set in14_min  3.0 * 0.90
    set in14_max  3.3 * 1.10


chip "via686a-*"

    label in0 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10


chip "adm1025-*" "ne1619-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "VCC"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
# Depending on how your chip is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp1 "CPU Temp"
    label temp2 "M/B Temp"


chip "lm87-*" "adm1024-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10

    label temp1 "M/B Temp"
    label temp2 "CPU Temp"


chip "it87-*" "it8712-*" "it8716-*" "it8718-*" "it8720-*"

    label in8 "Vbat"


chip "fscpos-*" "fscher-*"
#FSC "Hermes"

    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"

    label temp1 "CPU Temp"
    label temp2 "M/B Temp"
    label temp3 "Aux Temp"


chip "fscscy-*"
#FSC "Scylla"

    label in0 "+12V"
    label in1 "+5V"
    label in2 "+3.3V"

    label temp1 "CPU0 Temp"
    label temp2 "CPU1 Temp"
    label temp3 "M/B Temp"
    label temp4 "Aux Temp"


chip "fschds-*"
# Fujitsu Technology Solutions, "Hades"-Chip

# Temperatures
    label temp1 "CPU Temp"
    label temp2 "Super I/O Temp"
    label temp3 "System Temp"

# Fans
    label fan1 "PSU Fan"
    label fan2 "CPU Fan"
    label fan3 "System FAN2"
    label fan4 "System FAN3"
    label fan5 "System FAN4"

# Voltages
    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"

chip "fscsyl-*"
# Fujitsu Technology Solutions, "Syleus"-Chip

# Temperatures
    label temp1 "CPU Temp"
    label temp4 "Super I/O Temp"
    label temp5 "Northbridge Temp"

# Fans
    label fan1 "CPU Fan"
    label fan2 "System FAN2"
    label fan3 "System FAN3"
    label fan4 "System FAN4"
    label fan7 "PSU Fan"

# Voltages
    label in0 "+12V"
    label in1 "+5V"
    label in2 "Vbat"
    label in3 "+3.3V"
    label in5 "+3.3V-Aux"

chip "vt1211-*"

    label in5 "+3.3V"

    label temp2 "SIO Temp"


chip "vt8231-*"

    label in5 "+3.3V"


chip "smsc47m192-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "VCC"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10

    label temp1 "SIO Temp"


chip "lm85-*" "lm85b-*" "lm85c-*" "adm1027-*" "adt7463-*" "adt7468-*" \
     "emc6d100-*" "emc6d102-*" "emc6d103-*" "emc6d103s-*" 

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
# Depending on how your chip is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp2 "M/B Temp"


chip "emc6w201-*"

    label in2 "+3.3V"
    label in3 "+5V"

    label temp6 "M/B Temp"


chip "pc87365-*" "pc87366-*"

# Voltage inputs

    label in7 "3VSB"
    label in8 "VDD"
    label in9 "Vbat"
    label in10 "AVDD"

    compute in7   @*2, @/2
    compute in8   @*2, @/2
    compute in10  @*2, @/2

# These are the operating conditions as recommended by National
# Semiconductor
    set in7_min   3.0
    set in7_max   3.6
    set in8_min   3.0
    set in8_max   3.6
    set in10_min  3.0
    set in10_max  3.6
# Depending on the hardware setup, the battery voltage may or may not
# be monitored.
#    set in9_min   2.4
#    set in9_max   3.6

    label temp3 "SIO Temp"

    set temp3_min    0
    set temp3_max   70
    set temp3_crit  85


chip "adm1030-*" "adm1031-*"

    label temp1 "M/B Temp"


chip "w83627thf-*"

    label in3 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    # Internal resistors
    compute in3  @ * (1 + 34/51), @ / (1 + 34/51)
    compute in7  @ * (1 + 34/51), @ / (1 + 34/51)

    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
# The battery voltage may or may not be monitored.
#    set in8_min  3.0 * 0.90
#    set in8_max  3.0 * 1.10


chip "w83627ehf-*" "w83627dhg-*" "w83667hg-*" "nct6775-*" "nct6776-*" \
     "nct6779-*" "nct6791-*" "nct6795-*" "nct6796-*"

    label in0 "Vcore"
    label in2 "AVCC"
    label in3 "+3.3V"
    label in7 "3VSB"
    label in8 "Vbat"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  3.3 * 0.90
    set in3_max  3.3 * 1.10
    set in7_min  3.3 * 0.90
    set in7_max  3.3 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.3 * 1.10


chip "w83627uhg-*"

    label in2 "AVCC"
    label in3 "+5V"
    label in7 "5VSB"
    label in8 "Vbat"

    set in2_min  5.0 * 0.90
    set in2_max  5.0 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in7_min  5.0 * 0.90
    set in7_max  5.0 * 1.10
    set in8_min  3.0 * 0.90
    set in8_max  3.3 * 1.10


chip "f71805f-*"

    label in0 "+3.3V"

    set in0_min  3.3 * 0.90
    set in0_max  3.3 * 1.10


chip "f71872f-*"

    label in0 "+3.3V"
    label in9 "Vbat"
    label in10 "3VSB"

    set in0_min   3.3 * 0.90
    set in0_max   3.3 * 1.10
    set in9_min   3.0 * 0.90
    set in9_max   3.0 * 1.10
    set in10_min  3.3 * 0.90
    set in10_max  3.3 * 1.10


chip "k8temp-*"

    label temp1 "Core0 Temp"
    label temp2 "Core0 Temp"
    label temp3 "Core1 Temp"
    label temp4 "Core1 Temp"


chip "dme1737-*"

    label in0 "5VSB"
    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in0_min  5.0 * 0.90
    set in0_max  5.0 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch311x-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
    set in4_min 12.0 * 0.90
    set in4_max 12.0 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch5027-*"

    label in0 "5VSB"
    label in1 "Vcore"
    label in2 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    label temp2 "SIO Temp"

    set in0_min  5.0 * 0.90
    set in0_max  5.0 * 1.10
    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "sch5127-*"

    label in2 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in5_min  3.3 * 0.90
    set in5_max  3.3 * 1.10
    set in6_min  3.0 * 0.90
    set in6_max  3.0 * 1.10


chip "f71808e-*" "f71808a-*" "f71862fg-*" "f71869-*" "f71869a-*" "f71882fg-*" \
     "f71889fg-*" "f71889ed-*" "f71889a-*"

    label in0 "+3.3V"
    label in7 "3VSB"
    label in8 "Vbat"

    compute in0  @*2, @/2
    compute in7  @*2, @/2
    compute in8  @*2, @/2


chip "f71858fg-*" "f8000-*"

    label in0 "+3.3V"
    label in1 "3VSB"
    label in2 "Vbat"

    compute in0  @*2, @/2
    compute in1  @*2, @/2
    compute in2  @*2, @/2


chip "f71868a-*"

    label in0 "+3.3V"
    label in7 "3VSB"
    label in8 "Vbat"
    label in9 "5VSB"

    compute in0  @*2, @/2
    compute in7  @*2, @/2
    compute in8  @*2, @/2
    compute in9  @*3, @/3


chip "f81865f-*"

    label in0 "+3.3V"
    label in5 "3VSB"
    label in6 "Vbat"

    compute in0  @*2, @/2
    compute in5  @*2, @/2
    compute in6  @*2, @/2


chip "adt7473-*" "adt7475-*"

    label in2 "+3.3V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10

    label temp2 "Board Temp"


chip "adt7476-*" "adt7490-*"

    label in1 "Vcore"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "+12V"

    set in2_min  3.3 * 0.90
    set in2_max  3.3 * 1.10
    set in3_min  5.0 * 0.90
    set in3_max  5.0 * 1.10
# Depending on how your ADT7476 is hardwired, you may or may not have
# +12V readings.
#    set in4_min 12.0 * 0.90
#    set in4_max 12.0 * 1.10

    label temp2 "M/B Temp"

```

---

### Post by TheFu on 2023-03-07
13th gen is really new. I suspect the support chipsets are new too.  You may have to wait a year, if there isn't a solution now.  You can always try newer kernels, but I wouldn't suggest that to someone new, since there are liabilities and complexities in doing that.

BTW, the chipset and CPU are NOT the same thing.

---

### Post by MAFoElffen on 2023-03-08
Easy way to check if your system has working fan sensors with *logging* in /sys... If it does, it is in a file called 'fan*_input"... Unfornately, sys is laid out differently for each system, based on differing hardware combinations it boots on.

So first look for that file in /sys
```

find /sys -name "fan*_input" 2>/dev/null

```
If it finds a file, instead of null, then display it
```

grep . $(find /sys -name "fan*_input" 2>/dev/null )

```
For example
```

mafoelffen@Mikes-ThinkPad-T520:/$ find /sys -name "fan*_input" 2>/dev/null
./sys/devices/platform/thinkpad_hwmon/hwmon/hwmon3/fan1_input
mafoelffen@Mikes-ThinkPad-T520:/$ grep . $(find /sys -name "fan*_input" 2>/dev/null )
1981

```
If you wanted to see it update live at 1 second intervals, then 
```

watch -n 1 'grep . $(find /sys -name "fan*_input" 2>/dev/null )'

```
<Cntrl><C> to exit it...

But note that not all CPU's / Motherboards track that... For example
```

mafoelffen@Mikes-B460M:/sys$ grep . /sys/class/dmi/id/board_vendor
Gigabyte Technology Co., Ltd.
mafoelffen@Mikes-B460M:/sys$ grep . /sys/class/dmi/id/board_name
B460M DS3H AC-Y1
mafoelffen@Mikes-B460M:/sys$ grep -i 'model name' /proc/cpuinfo | head -n 1
model name    : Intel(R) Core(TM) i9-10900 CPU @ 2.80GHz
mafoelffen@Mikes-B460M:/sys$ find /sys -name "fan*_input" 2>/dev/null


```
My server doesn't track that in /sys... And shows as "N/A" in inxi... But it shows in it's UEFI BIOS system UI.

I don't know (yet) where the BIOS tracks that. I know section 27 of the SMBIOS DMI Tables is Cooling Devices:
```

mafoelffen@Mikes-B460M:/sys$ sudo dmidecode -t 27
[sudo] password for mafoelffen: 
# dmidecode 3.3
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x002C, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0029
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

Handle 0x002F, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0029
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Not Specified

Handle 0x0037, DMI type 27, 15 bytes
Cooling Device
    Temperature Probe Handle: 0x0036
    Type: Power Supply Fan
    Status: OK
    Cooling Unit Group: 1
    OEM-specific Information: 0x00000000
    Nominal Speed: Unknown Or Non-rotating
    Description: Cooling Dev 1

```

---

### Post by ricciolino on 2023-03-08
> **TheFu said:**
> 13th gen is really new. I suspect the support chipsets are new too.  You may have to wait a year, if there isn't a solution now.  You can always try newer kernels, but I wouldn't suggest that to someone new, since there are liabilities and complexities in doing that.

BTW, the chipset and CPU are NOT the same thing.

Yes I know the chipset and CPU are NOT the same thing, but I just wanted to provide details on which my CPU was, since for this particular topic I think it was relevant.
About the chipset, how can I find the exact model number and revision?

---

### Post by ricciolino on 2023-03-08
> **MAFoElffen said:**
> Easy way to check if your system has working fan sensors with *logging* in /sys... If it does, it is in a file called 'fan*_input"... Unfornately, sys is laid out differently for each system, based on differing hardware combinations it boots on.

So first look for that file in /sys

I can confirm that it seems I have no working system fan sensors on my system.
The following command provide me a null output:
```

> sudo find /sys -name "fan*_input" 2>/dev/null
> 

```

---

### Post by TheFu on 2023-03-08
> **ricciolino said:**
> Yes I know the chipset and CPU are NOT the same thing, but I just wanted to provide details on which my CPU was, since for this particular topic I think it was relevant.
About the chipset, how can I find the exact model number and revision?

Look on the motherboard?  Read the specifications from the motherboard vendor's website?  inxi and/or lshw might have it too. IDK.

BTW, I ran that find command about 10 minutes ago on 3 systems here. 2 Ryzen and one Core i5. They've never returned.  Had to cntl-c to break out.

---

### Post by pqwoerituytrueiwoq on 2023-03-08
This is the file i used when i was using 4th gen intel
```
[FONT=monospace][COLOR=#000000]$  cat /etc/sensors.d/nct6791-isa-0290  [/COLOR]
chip "nct6791-*" 
 label in0 "CPU Input Voltage" 
  compute in0  @ * 2, @ / 2 

 label in1 "+5.0V" 
  compute in1  @ * 3, @ / 3 
  set in1_min 5 * 0.95 
  set in1_max 5 * 1.05 

 label in2 "AVCC" 
  set in2_min  3.3 * 0.90 
  set in2_max  3.3 * 1.10 

 label in3 "+3.3V" 
  set in3_min  3.3 * 0.90 
  set in3_max  3.3 * 1.10 

 label in4 "+12.0V" 
  compute in4 @ * 12, @ / 12 
  set in4_min 12 * 0.95 
  set in4_max 12 * 1.05 

 label in5 "CPU Digital IO Voltage" 

 label in6 "Vcore" 
  set in6_min 0 * 1 
  set in6_max 1.32 * 1 

 label in7 "3VSB" 
  set in7_min  3.3 * 0.90 
  set in7_max  3.3 * 1.10 

 label in8 "Vbat" 
  set in8_min  3.0 * 0.90 
  set in8_max  3.3 * 1.10 

 label in9 "CPU Digital IO Voltage" 

 label in10 "Intel GPU" 

 label in11 "CPU Analog IO Voltage" 

 label in12 "CPU Cache Voltage" 

 label in13 "System Agent Voltage" 

# label in14 "???" 

 label fan1 "Chassis Fan 1 Speed (VRM)" 
 label fan2 "CPU Fan 1 Speed" 
 label fan3 "Chassis Fan 3 Speed (in)" 
 label fan4 "Chassis Fan 2 Speed (out)" 
 label fan5 "Power Fan Speed (nc)" 
 label fan6 "CPU Fan 2 Speed" 

# label SYSTIN "M/B Temperature"
[/FONT]
```

this is the file i am using for my AM4 X470 ryzen 3000 based system
```
[FONT=monospace][COLOR=#000000]$ cat /etc/sensors.d/nct6795-isa-0a20  [/COLOR]
chip "nct6795-*" 
 label in0 "Vcore" 
#  compute in0  @ * 2, @ / 2 

 label in1 "+5.0V" 
  compute in1  @ * 5, @ / 5 
#  set in1_min 5 * 0.95 
#  set in1_max 5 * 1.05 

 label in2 "AVCC" 
  set in2_min  3.3 * 0.90 
  set in2_max  3.3 * 1.10 

 label in3 "+3.3V" 
  set in3_min  3.3 * 0.90 
  set in3_max  3.3 * 1.10 

 label in4 "+12.0V" 
  compute in4 @ * 12, @ / 12 
  set in4_min 12 * 0.95 
  set in4_max 12 * 1.05 

 label in5 "???" 

 label in6 "VIN4" 

 label in7 "3VSB" 
  set in7_min 0 * 1 
  set in7_max 1.32 * 1 

 label in8 "3BAT" 
  set in8_min  3.3 * 0.90 
  set in8_max  3.3 * 1.10 

 label in9 "CPU +1.8V" 
  set in9_min  3.0 * 0.90 
  set in9_max  3.3 * 1.10 

 label in10 "???" 

 label in11 "VIN6" 

 label in12 "SOC" 

 label in13 "DIMM" 
  compute in13  @ * 2, @ / 2 

 label in14 "VIN7" 

 label fan1 "PUMP 1 Speed (Rear)" 
 label fan2 "CPU Fan 1 Speed" 
 label fan3 "Chassis Fan 1 Speed (VRM)" 
 label fan4 "Chassis Fan 2 Speed (Bottom)" 
 label fan5 "Chassis Fan 3 Speed (Front)" 
 label fan6 "Chassis Fan 4 Speed (Front)" 

# label SYSTIN "M/B Temperature"
[/FONT]
```

to figure out most of these what i had to do was compare value between hwinfo in windows and my changing bios settings to see what changed then adjusting the multiplier/divider

you need to load the module in the kernel to get any sensor data eg:

[FONT=monospace][COLOR=#000000]```
$ cat /etc/modules [/COLOR]
# /etc/modules: kernel modules to load at boot time. 
# 
# This file contains the names of kernel modules that should be loaded 
# at boot time, one per line. Lines beginning with "#" are ignored. 

nct6775 
drivetemp
```

my system does also have these ```
[/FONT][FONT=monospace][COLOR=#000000]nct6683  nct7802  nct7904
``` no idea what one you need on 13th gen intel, i think i used it87 back in the AM3 days, maybe you want one of these but i doubt it[/COLOR][/FONT][FONT=monospace] ```
[/FONT][FONT=monospace][COLOR=#000000]it87         it8712f_wdt  it87_wdt     it913x       itd1000      ite-cir      itg3200[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]
```[/COLOR][/FONT]

---

### Post by ricciolino on 2023-03-08
> **TheFu said:**
> Look on the motherboard?
Do you mean using a magnifying glass on a specific component soldered on the motherboard to read the component label?

> **TheFu said:**
> Read the specifications  from the motherboard vendor's website?
Seeing at this, I can state that my "chipset" is the one named "Intel Z690 Chipset", but I am unable to find some specific code (like a kernel patch or similar) around the web to read the RPM value of the fans.


> **TheFu said:**
>  inxi and/or lshw might have it too.
lshw also confirm the chipset model:
```

> sudo lshw | grep -i chipset
             product: Z690 Chipset LPC/eSPI Controller
> 

```

[IMG]https://ubuntuforums.org/image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAdwAAAFICAYAAAD6VE gAAAABHNCSVQICAgIfAhkiAAAABl0RVh0U29mdHdhcmUAZ25vbWUtc2NyZWVuc2hvdO8Dvz4AACAASURBVHic7N15vFVV/f/x17lciFkERYTrV0UQTE1USEvNUjT9JYXfLEVzpiRHNHG2SDMp 1amaBkkGlpaOZQogeZc5gAOJCKIAyogILPMfH5/fPaJfffd5559hrvP5dz3k8d6cPc 66619nD2Z6 117knAxgiIiLSpGoq3QAREZGWQAFXREQkBQq4IiIiKVDAFRERSYECroiISAoUcEVERFKggCsiIpKC9ANuHf7J34Gp1ywiIlIxyQLujDLWuBq4A1hcxjJFRESauQy5/tLUSOBl4Ak84O4FDAM2Afem0zgREZFqkbuH yfgBOAuoCvwMLAHMLnImvbCQ3s2NTakfCEwB1gLfAjcHZPnYGAKsAhYB7wGnFRk20RERJpY7oD7AXAd0AXoDrwP/BxYUWRNM/D 9E558g0GfgZcBuwGHAPMjMnXCw 4R M3Ar8Gfo8HYhERkWamNucrFwFHAaOAnYE/A5OAnwIPNmGLdgM AR7Bn/d AEyLyXdPZHkscAYeoJ9pwvaJiIgUIXcP9w/AkcArwfIU4IvAszF5LwI2htKRJbToQXyY C1gInAB0CMmX1fgJ8CLeO97AT5s3bmEukVERJpI7h7u/NDPtwT/byB dvEE/Blv1rwSWrQA6A8cChwCnAtchQfThaF8dwPdgIvx570b8WCtTxaLiEgzlHuWclOpwwPyILx3mk9nYCnwTeAvwboafKLU8cB9wbo2 PDzX4ARZWyviIhIGeTu4VbKccAOwJPAcjzQbqb Z4E3473awcADQCvgBnyYWUREpBlKbwB2Mt6Xzg43vxAsR/ oxnL840hPA28AJ JBeFYk3zBgH7xXOwtYhQdpERGRZij9IWUREZEWSFOMREREUqCAKyIikgIFXBERkRQo4IqIiKRAAVdERCQFCrgiIiIpUMAVERFJgQKuiIhIChRwRUREUqCAKyIikgIFXBERkRQo4IqIiKRAAVdERCQFLTPgzgEuq3QjilSHf7/TwBZSb0sxAXioCcot5rhtze8PkWasZQbcrdlq4A5gcZnKWwyMqEC9afslHnii6bRIvrbAtXjQWYN/f/O9wM45yr0TWAeMKnuLy2NrP24iVUQBd2uzFA8S77SQesvlBmBf4KJg avB8l8j W4EzgSuBAYBZwALge4xZbYGhgC/Ao4rf5PLYms/biJVpPoDbhtgLLAMWAJc3Ujek4EZwFpgNt5ridtDF I9oLXAh8DdOcrrgQ8VLsR7S9PwC3TUCLwHchgwHe8xvY9f8LP2on7PLNcQ4URgCt7zWgzMBy6J5OkSKqcbcGtoeXgkb9J6M8DlwHvAemAmcGJMvnHAVDywLQAWAdflKBOgMz4s2raRPEl8ALwMvB0szwyWP47kOw74KXAPfi5MBc4DXogpczDeg7wB3y87ldjGWuA2YBV zlyVI185z5ek749a/MYim 8qcg89J30fibRAcQNt1ZNGY3yMMQRjT4xJGBsxLovkG46xAuMkjF0xjsL4EOP8SL7BGJswjsPohbEfxtUx9bbHmIXxMsbhGH0wvoFxYUzeERifYDyDMQijA8ZBGP1i8tZhGMbAHNs7MXj9LIwMxv4YKzGG5si/OKg/337MV 8ZGGsxTsXoi3FlkP ASL5xwf4/C6MG47Ag3yGNHD9rpP2FpqFBeX1yvD4b4z6MdgnKGo/x2 DnFzBGltCuCcF  RV 3E/BWIdxfEzecp4vSd8fV2IsxfgaxqcxHsDYEJMv6ftISallpoo3oGnTRxg/DC3vhLGZhheKeRiXRtZdjPFqZN1ZeADrkKfe0/EL0i4J2jgCvygOSpA3ScCdG1l3O8aUHPnLFXCn4wEovO55jLsi68ZhvBlZ9ybGqBzljibdgPslPECsxHgY4yKMnjH5aoN99/Vg YcYT5fQrgkYC4Nys vuxngqJm85z5ek748FwbHILu I33gW z5SUmqBqboHeroA2wOvhNbNw4fEwrrjw5ZjqL97bgB6R/I iA DvoUP316ADx1H7QvMJfmzs/XASwnz5jM7ZrlvmcrOpQ8 RBs2Hdg9Ju87keUVQNcc5Y7Gh6sfKKFthXgc2AUYCjwPfAt4A/hCJN8XgW2AR4Plh4HPAzuWUPdMYGNo VVyH7dynC9J3x/bADtQ//jOx98HYYW8j0RaoOoOuBb8vyGyPrqcCf4/Nvg5nDpG8i4A uPPqeYC5wKv4RekaJlGciuBzQXkb0zryHItW7axKUW3N9c iNvONNqX1HrgMTzY7w/8E/h JM9x H5diD rfBJ/N/1vCfXG7b9cynG JH1/5BJtXyHvI5EWqLoD7nL8LrxPaN02NJxxuhCfVHN4wnLX45Npvo9fkLsCB0fyTAN2I/fHSZrSnngwyNqHhr3erHU0DNDFmIP36sMGBOtL0QXvcbYvsZxiGT7RqnNoXQ3eA74G38Zsuhf4egl1fZr6x21vYFYJ5eWT9P2xHH PhI9vD2C7SL5C30ciLUx1B1yAW4CzgZ741o4GWsXkuwaf/Xk53oMdgA8XR2fQHgecg88C3Qn4Nt7TmBHJdw/eA74Pn03aG5 hfF6J25NEN AXQD/8Yy1D8JnIcWYBX8Evsm2J3zdJjAVOAk7Fh0GzH6u5qcjyskbiAe/IEsvphR/TXYPlPYLl6FD2o8D3gEOAz DH jTgb6E8h AjGvfgw83ZdD8 9Lx9kW3sBvwcP26n4MF7bJFlJZX0/XETcD5 Lu0O3Ex8Tzjp 0ikhar4g QmTW0wbsFnYs7GGINPKopO9gDjW/jkn7UYSzAeZ8ukmGw6Ap8csxRjNcZL MzNuLp74JNhPsJYg89Y/mpMvhH4BJzGtmMyFvtvRiTfRHym6YSgfQswLm k3P3xGbZrgvKGF1lvBuMqfNLMBnyG9ikx9Y0LygyvezE4LnHtG015Jk39Msd2nBbJdxHGc2w5vq/j50pNKM vMD6IqaMrPpHoO0W0b0KwX36LsQqfQHVFjrzlPF Svj9aY9yEsTzIe2mQL27WfZL3kZJSC0yFPmmU5m4i/rxsaKUbIlWtFp/sdiLpTWgT2crV5s8iIi3ervhw VT8uf8l F xmlrJRolsXar/Ga6IlK4VPiN/Fj4Rbj/gy/hf2hKRRDSkLCIikgL1cEVERFKggCsiIpICBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAFRERSYECroiISAoUcEVERFKgv6UskoKeta3Z91MdWLxpA/9eq7 HKNISqYebpjnAZZVuhJTDzdvvzBN1/Tm4XadE fds045R2/bg E7RL AVkbzmsOVL7m4uQ74KUcCtVovxLwJPy2RyfwvkgZG8n8W/6H1lkJ4COkfydAVuAz4A1gIvAofnqPsM/I22DngZGFzapmxbU8v3tu3Bn3fsw6O9 nHvjrtxUqdupRXajP1PbRueqOvPpJ67l17YxST76 y/Zsv5sRF4F/gN0D0mby/gDmAhsAZ4HTgzT/mtgNnAVYla3VBb4Fr8vFoDzAPuBXaO5Eu6Hb8k/r1xWpHtg L2S7mkfX3pg//l/8fKlK9CNKQs5XE2DYPmLfiFZ0Zo3V7AE8BfgeOB5cDeNLxIjwc A5wEvI8H1UlB3tmhfEcHea8OyrwA Fvwu F8CXXI1HBz9/ hV20bABZv2ki3VrV8tm0H7lq5pPACA1M/WcHUT1YU/ftV6T38G4daAfviQakvcFgoTzfgn8Ay4NvB7 wD5Ls3OBHYHripyLbdCAwBLgT A wIfBU/n98tYjtuACYAXwJ HpQ1L/jdYhS7X6TiUv/W 1TTRIwpGHdiLMaYj3FJjrwjgjyHYUzHWIfxPsagUJ4MxuUY72Gsx5iJcWJMWW0wxmIsw1iCcTXGHIzLIvnGYUyOrHsRY0xMmT0wJmAsxFiDMQ1jSOj1LljOf8NzbHNnjDqMtmXe7ycH 2dQZP0fMR7N87utg989O7L zZj9Mhnj8dBybXCMbyiu3d/q1M2eqOtvD/bsa7u1/pQB1i5TY4e171wv383b72xP1PW3b3XqZuN32NUm99rdrunWy9pmaurlO7bjtvZEXf//pp9vv1NsvX/t2deeqOtv3 jY1e7u0dum9upn129XZ51rWtXL1zZTYxd22cH vGMfm9qrn92/Yx8bs12dtY/UW0vGzuy8vd2z4242pVc/u7NHbzu5UzerJfPfPP3atK3XtnD6Ube64o77xcH5li/fr/H3Q3jdJcHvbhtadwPGaoxuBbShBn9f/rCRc3MGxlqM2Rijgt8J51mCMbKM25FNQ4PX hR3fha8X5Jer8ZhTMW4EWMBxiKM6yJ5Cr2 lPN6mk2PYtycYP8kyZfkPEi6HQlTyxhSPgJ4Fr/jPQbvDQ3Nkbc9cA3wHXxY83gg3DE5HfhBUMaewETgLuCASDlXAMOAk/Ev7j4Q2KWEbWgPPAkMwO/e9waux4dQspbhwykZYAnw3dDyuBzlXoTfaR9VQtuidsafn1wNvBB57TB8Ox4APgKm4/s6rFWQ1kfWrwUGRdYdADwdWt4IPEfD45HQZ9t2AODBVUt5a8M6ANbYZv6Ro3d6UuduLN20kQwZvtCuE1/psE291 duWMf9q5byYsKJUqd27saza1exYNMGPte2I9/dpv7Y5JnbbMfXOm7Lok0b MPKJfxr7Wr6tW5L25r6b VRXXtwcudurDPj0aDtZ26zPWd32VLesk2buH/V0v/2vDeYcf qpdy/ainPrV2VqL1lld1FbUPrhgAP4 dzUt/Eh1tvjHltODAWf /sAZyH92LPjeT7GH/ftiug3qy47Si3pPsl6fUKvPf9OtATv 5dARwSer2Y60u5rqfllvQ8yMq3HQUo7U6ruaeJGHMj627He71xdzKW585lOsb4yLrnMe6KrPuI nfYO2Fspvge7ukYGzB2Sbjdi4PtyZdvdLDNQ8u0v2swnsTvMKN3i62Dupbhd7UDMC7A2IRxQiTv08F 6IXRCuPUYPtfjSnvXIxhGEsx9sd7HbOKa/89O 5mT9T1ty 269RovmwPd/g22xtgZ3be3p6o62 XbbtjbP4j2ndO1MM9tuO2Btj/1LaxJ r629Re/er1Sn 63U72RF1/G9apq2WCdbWZjLUK5dmhVWt7vK6/PdSzr7ULer7tMzU2udfu9o 6/g164dm6JvXcvfTjX0wPtyY4F2ZjvB7Jtxbj/wqoP4PxGsaPc7w D PSmDa/Gln3JYwPMVZiPIxxEUbPErYjm8rVw026X5Jer8bhI0jhdW/ivb64cpNcX8p5Pc2mcvVwk54HSbcjYWoZPdzos7zZ DOWOOuBlxopqw8 MSdsOvWfnXTBe9OvhNbNo7C79Kh9gbnAOyWUEWc0fof6QJnKuxT4NN6z3xx5LXu2PYffWb6M90L jj jDTsdnwT1fvD/mcCfI2Vmgv9r8clX7 GTR9qUYTsSenP9WgAWbdoAQLua0t5SM9evAeC9jev5xDbTOpNh 9otUy3 scZvq8/apjsP9uzLtd16sf n2rMJ 2 ePm0 RQboWNOKR3rtzhN1/Xm41 60zdRQA9TVti6pjWWzGz4isQF/Dy0CjovJZzHrcvlfYFf8OWlUd6AOGEP9y ANQO9I3sfxEamhwPPAt4A38F5vsdtRbkn2S5LrVdY7keUVeG uFOW4npZbIedBVr7tSKhlTJqKXl9q2XKxjlpJw0ARFT3RM5F12Z83RPJFl PKAh9OjYrW0RzthwfwrwPzY15fh /fNyLr36LhDOQ5wEFAxyAtwIfQ3g/lWY8Pc3XHJ6o8FKzfDp 5WYSFGzewQ6vW9G79KZ5YszJv/nynSqFqQydm9mcLHffJq5czb8N6Dm/fmX0 1Z5D2nXikHaduHrJBzwdae/yzZv466plDepYubncrS7SPOD/4cHqA/zciHqXhjODG3MVcCs izYqu2uPJdkN5np8tutjwA BR4Dv03AWfJLtKLdC9ku 61VW3GmR6zqZVDmup VW6HkAybYjgZbRw92T rcW 1DUDFbAA8G kXUDgvVZy/G73PDz1W2I/8jDUiD8Uc4a/O4rahp J530TbaOhjcacbrgd/LtE5abSzv8 ctv2BL44rxEw9GFXagfSMNW4cF2J/xZfHS6/7 BQ0PLtXigfj5JoxvK/lGKr3Xclt1afwqAdpkaDmsfnYLdNA5q1xGAgW070CaTYYMZizdt/O/rnWta8Z/1a/jVsoWcufBtbl3 EQCDgmfP4M NAdpmavjb6mWMX7Hov lfa1excFP9O7/1QURvlSn9 lqQ9fgM9jfIHaQm4TPRk/S0vgr0A36W4/WFeEDM9fGyxhjwNg1n4kOy7Si3pPslyfWqGEmvL/kU2r5VJHuu3li Us6DErWMHm434Bf4RJ6D8AkHJxRZ1tignKfwafnfxCfyXBDJdwv UZl78IAxmvie6wvA fgw7ExgJLBtTL578D acR8wCh/ 2RMPVnEffZgFfCX4vRV473pTTL6R KSFQu724vw0aPfd Bsm7D18Egr45xb/gO vyfgQ3dHAKZHf SzeY34F2AH/TOQ8Gk7OuBHv V6BfxzofKADHviL8MCqpXylwzb0rG3D B12ZfGmjWzbqhUz1q3JOXGqMd/dpjutMhl2Dj5mVFfbhnO77ADA31cvZ/aGtfXyH9txWz7zqfb0DoL9Y5 sYGPodv 8LjuwU20bXl /htWbN3Noe79bm7dhywyz Rs38OgnKxjcvjO377Ar09atJkOG3q3b0CZTw3Hz61/NFm/ayBrbTLtMDT/ero4PNm7g7Q3rmLS6Ye84seg5AH5 ryuwnDH4BJXH8N7lPLZ8/OXKSN6r8M9uNza6cQ3 Hv4QuB f2HQofjMcLu9RvEf7PH4DfQj mdkfF9j rF74Y6Zdg U98JGb8HujEEn3S9LrVaGSXl/yKbR9z Hv8f3wY7gcf4xUaL6k50GZtYyA 3e8FzkNvwP9AR64ijEe6AH8KPh/LnAq8K9Ivh z5TOoS4C/4HfIUffhd1rP4CfFRBo 0wD4BD8hxgB/DLZnFv5mizMKD27v4ifTt8k9k7AchuD7I7ofwJ/HTgh vge/AboI Al 43ABHqjDNuKzIHfHt30KcAkNexCP4DMOr8CP6xtBW4ocwVhtmznno/c4Y5vt FzbjnSpacWSTRt5vsg/x/i/HbeldWZLv7F7q9Yc19HvqF5fv6ZBwL1x2UJO7NSNVmR4ds0qbgl6sFnT1q2mrrY1g9t3pl2mhqWbN3Lvyo 5b9XSevnGLJ3P xvXM7h9Zz7XtiPrzJi/aT2PrF7eoI0bMf5v6QJO77wdn23bgVZkeGbNqtIC7vSYdXvQ8HFCPh8Bn8PfT7/Dz/u5 PO2sKPxz17n vRB1m34 fQ9/HxZDbxKw79K9DB 8b8KnxPwLj6s/NMC2581ivpB5K/B/ H3RiGS7pek16tClev6Umj7bsKP85P4Dct3g3YUmi/peVBmW8OTwdJMxHd4vjeiSAX9tWdfOte04vSFb/P2hkK7gcI/8SB/TqUbIpJby jhikj16oqPgPy20g0RaZwCrohs3T7G50iINHPVP6QsIiLSDLSMjwWJiIhUmAKuiIhIChRwRUREUqCAKyIikgIFXBERkRQo4IqIiKRAAVdERCQFCrgiIiIpUMAVERFJgQKuiIhIChRw0zQH/05bKZ85 B8nNZr8q7WkAHX4MRlY6YaINB8KuNK4X7IloIXTaSWWuxgYUWIZAH3wvwj WBnKyuoF3IF/kfka4HXgzDKWvzVLetxW4/twcdM2R2Rrom8LksbdgH9B9peAnwNfBeYB71WwTU2pG/7dqsvwL9V D9gH2L2SjdoKLaX0mzKRKlPdPdw6YDNwaGT9eXjvJXq7cTIwA1gLzAZG0XAPjQOmAjcCC4BFwHUxdbcBxuIX7iXA1TnamAEuxy/s64GZwIk58o7AewyH4V 2vQ54HxgUk7czvv1tc5SV1AfAy8DbwfLMYPnjSL4k 6ULW3rI3YBbQ8vDY pOcjzK7TJgO3wf/xXf1juAKyP5yn3cJuLf6XpnkHc cElMWeWu9 Cg3kXB668BJ0XKKeS47UX9kZBcQ8pJtyPp 01kKxE3YFg96QmMX0fW/RPjV5F1wzFWYJyEsSvGURgfYpwfyTcOYyPGWRg1GIdhGMYhkXyjMT7GGIKxJ8ak4Pcui Q7A2MtxqkYfTGuDMo7IGZbRmB8gvEMxiCMDhgHYfSLyTs6KGdomfbj0KC8PjleT7pfsmlxsD256kt6PLLpUYyby7Cdb2D8KUG ch 3icHvn4WRwdgfY2XM8St3vcdjXIwxEKM3xjkYmzEOLvK4ZVNd0K6BJe6/Qs8rJaXmnSregKZN38YvEq2D5V2If2PPw7g0su5ijFcj68ZhvBlZ9ybGqMi6jzB GFreCb QRQPudIzxkXXPY9wVsy0jgrYPSrDdo0k/4CbZL9mU78Kd9HhkU7kC7lqM/0uQr9zHbSLG3Mi62zGmNHG9cekljDFFHrdsyhdwk25HoeeVklIzTtU9pAzwJ6ATcESwPAx4C/h3KE93fPh1DPV3zw1A75gy34ksrwC6hpa7ANsDr4TWzcOHlqP64MOWYdPJ/cxwPfBSjtfCRuPDdg8kyFsu70SWo/slqUKPR7lZgjxNcdxmxyz3beJ6uwI/AV7Eh5sX4MPCnfO0tVSFbMc7keVizyuRCqv gLsMeBg4IVgeBtwVyZMJ/j82 DmcOsaUuTlmXSb0c/aCvSGSJ7oczR8uK9dFf2WO puDfPslqUKPRzm9C ycMG 5j1vryHIt8fuvnPXejT/jvRg4EBiAB8I0rgxJt6Nc55VIhVV/wAUPsEPxCRx74xeZsIX45KDDy1TfcnxyR5/Qum3wnlvUHGDfyLoBwfpSdAF2AdqXWE5TWUfDAJNVzPFYBbQrtVHAJOBo8vegmuK47Un9iXz70LDXW856a/B9fD3wBN7D/ZjGRxEaO26FaKrzXqQZaxkB9yH8Lvl3 NDZrJg81 CzOi8H uNv/gsofkbkLcDZQE98L48GWsXkG4vPCj0VHz68Ep9FelOR9WaNxGcWH1liOb3wfbFrsLxHsFzqkN4s4Cv4TUhbGu6bQo/Hc3ig3A/oQfHBdwx w/QYMCSo99SYepviuHUDfgH0A84I6r 1CevdjAe4wfg52hoftm/s2OY7bkk11Xkv0sxV/EFyKul3 CSOCxvJ8y18MsdajCUYj2N8PZJnHMbkyLoXaTjJpA3GLfhM5dnB63NpOGkqg3EVPkloA8YsjFNytG8EPmklyfaOpjyTpn4ZlBP9d1qR yWb9sd4AWNNUN7wIo9HNnXAuBuf2Wskm9iTK/0PPolpUVD36xinN/Fxm4jPZJ AsRpjAcblMfnKXe8AjGcx5uPn53UY/6DhzP6kx20y8efLjCK3o9DzSkmpGafGnv6ISFom4s nh1a6ISLSVFrGkLKIiEiFKeCKiIikQEPKIiIiKVAPV0REJAUKuCIiIilQwBUREUmBAq6IiEgKFHBFRERSoIArIiKSAgVcERGRFCjgioiIpEABV0REJAUKuCIiIilQwM0aB0yuYP11 B/ZHJhSfXPY8qVRN5ex3GK2Yw5wWRnbUA41wG AJfj2jKtsc0Rk66eA21ysBu4AFqdUXx/8L2k/VuZy096OpHYG7gZmkyyAHoN/OfqRwLbAeU3aOhFpARRwm4ulwGnAO5VtRsma63a0BxYBP8R71PnsDnwAvAQsA9Y0XdNEpGWo/oA7EZgC3In3uuYDlzSS/yrgI/zifF3kte2AdcBxkfXfANYD3SPrL8Qv7muBD/EeVtRebBnazTcU2wOYACzEA8A0YEgkz8H49i4K2voacFIjZZZL0u1oA4zFg9gS4Oo85XbGh6nblti mcAF PmwupF84/D23wD0Zsv2aEhZREpU/QEX4AjgWWB7fKjwamBoTL6D8KB5OB5srwAOCb2 GHgAOD3ye6cBf8UDddZg4Gf4s8ndgnpnxtQ5Ax/a3SnPNrQHngQGACcCewPX40PDYb3wgHs0sAfwa D3eCBuSkm34wpgGHAy8AXgQGCXRvJfBMwDjiq9iYkMx7fjcuCt4OdMsF5EpAS1lW5AKt7GJ8CADxH GTgbD55hy4CRwGa8Z3ghHhCeDuX5LT65qifea 0BfBkPqGG7AZ8Aj A9qg/wHmmxjsd7XH3ZMlwbNzR6T2R5LHBG0L5nSqi/XM4GbgL FiyPAN6tXHNERNLSMnq4s2OW 8bkm4UH26xFQNdInsfwAHFKsHwyHkynRPI9GPz W/gw5gV4cC7WvsBc8j8b7Qr8BHgReB9YgA/3di6h7nLpgo8yvBJaNw8fWs5lNN7DjN4ciYhsZVpGwG0dWa7FL JRG2PWRfMZ8Du2DCufCoynfqAGD3T98YA8FzgX7zXvkLjVDdthCfLdDRwGXIz3zgcAL9M8jnS2/Rsi66PLIiJVqDlchpventQfPN Hhr3eQtyODxlfgD8nvT1HvvXAVOD7wP5477PYZ6nTgjp3biRPDf78 XrgCbyH zE FJ3LKqBdkW0q1HK81x9 7rwNDSebhXXBn/G2b7pmiYikoWUE3G7AL4B  PPMIcCtJZT3ITAJn8n6KD4sGnUccA4 nLsT8G28FzyjyDrvwXvK9 E92N74doQ/H7oZf647GD yrYM2RofFw57DJ1jthw95N3XwvQV/jtszaONooFUj Ufiz CPLLHeVnhvfwC jV2Dn/uXWK6ISEItI D HeiE9xJ/DPwAD1ylGI8HtAk5Xl8OnIBPuHoDn1l8HP6cOGwyPtSaDdovBMvRwPwJcCg LP1H4D/AtTSccDQM78F/ENS1Cp/dnMtNeG/4SfwjU6c2krcxSbfjx3ivf0bQvnV4QG1qnYDpQdodODb4Wc GRSQlSZ8Mbr0mAh2J/xhQKUbgHx3qhX/OVkREpBEt42NB5dQJRGMj AAAIABJREFUf6Z4Od7LVbAVEZEEWsaQcjn9Hv8s73Tgmgq3RUREthrVP6QsIiLSDKiHKyIikgIFXBERkRQo4IqIiKRAAVdERCQFCrgiIiIpUMAVERFJgQKuiIhIChRwRUREUqCAKyIikgIFXBERkRRUf8CdADxU6UYkUIf/kc2BZSqvBvgNsCQod1yZym2uyr3/JB0t7TyVFq36A 7WYjVwB7C4TOUdg3 37ZHAttT/ovpqlGT/fR54GFgapAeBnWPynQHMwb r92VgcI7yKpUvqUrUuzNwNzCbZAG0nOdpufefSBOwqk4TMB5qBu1IO12M8VYzaEdzScdhfIRxBkZXjG4YYzBmYrQJ5TsawzCuwvgMxniMNRh9I VVKl/SVKl698C4EeNbGLMxxuXJX67ztNzboaTUNKniDWjaNAFjMsZtGKswFuJvymi cUG 8LoX8YtyNO FGHMw1mJ8iHF3Ce3bC6v3b2COfOMwpuIXswUYizCuy5Ev7l/0wpfBuBzjPYz1eOA5sZF2dsaow2hb4vGYiDEF406MxRjzMS7JkbdHcPwW4hfPaRhDith/22F8jPH5mNemY3w5tDwZ4/HQcm3Qxhsiv1epfEmPR6XqDaeXyR1wk56nSVOh26GkVIHUMoaUB NfFL8/MAq4Gji hLJ BlwG7IYPic0soW0z8C9J3ClB3i8BrwM98fZfARwSyTM8KO9y4K3g50ywPux04Af4vtgTmAjcBRyQo 6LgHnAUQnamc8RwLPA9vj uxoYGsnTHngSGACcCOwNXA/0ieRLsv9OCcr6J9AZuA14E/gTvk3hMg8Ang4tbwSeo F qVS rHzHo1L1JpX0PE2q0O0QqYCWEXCX4BeKWcCdwF Ac4osazfgE AR4ANgGnBtGdqYxFx8gslm4B/4c7IDiyzrPDzA3hGUcx3wAnB 6c3M6218Owx4CfgzcHYkz/FAbzwQP4Y/m/sT8Isi6jsEmBz8fAuwI/BV4F7gy0Dr4LXWQBfgI2AY/px3f2AhsEOovErlS6pS9VZKtWyHVL2WEXBn4ne8Wa8CfYss60FgEX5XPhG4AOhRUuuSeyeyvALoWmRZffCJJWHTgd1z5B N90AeKLK sNkxy9HjsS9 g/FOGerbEe VZYBjgYuBN/AAHt6eTPB/LbASeA9YA7SJlFepfGGjyX08KlVvpRSzHSIV0DICrkWWMwnyALSKWbcA6A cjAeEc4HXSOdOenPMurhtSSpuv8Tth3JrHVmupeF2lLMtxpYzPYM/XshaE/p5PbAM6I5/lGwffAh/O7y3VOl8SVWq3kqplu2QqtcyAu6n8Yt61t748HLYUqBTaLkG/2xnnPXAVOD7 NBVV DgsrQ0PXPwXmTYgGB9nC7ALviz1VLtSf3jsQ8Ne73T8OH7nctQ37tBWYZfkEcF9e9Jw2fH/wYODS3XAgcBzzeTfFn5jkel6m0q5dpekQpqGQG3G/BzoB8 gebrwNhInhfw4PlpvBc0Ev9cYNRx PPfvfCJOt/Ge54zmqLhTWgscBL Gci wJXAIOCmHPlH4s9ejyxD3d3wZ7H98M9ODgFujeS5Bx9BuA84DH eO4TiPqf5KH7cAEbgF 83gRuBx/HPbWbdiH9e9wr8xuxWoAP zJlmkC8r3/GoVL2t8Bu3AUA7/GZ0AD4qVIpyba9IhVV8qnSTpgn4RwZ y5aPBV0Rk68Vxq/xj4 8jXEt8R8LOgLjaYylGKsxXsL4Wgntm0z8xyNmRPIV8rElMC7DP7qUq94M/vGoeRgbMGZhnNJI/tFBu4aWeDwmYkwKjstq/CNOl fIm/1Y0Ef4x4JexvhqEfuvHca7GKclbOOZ GdD12G8gh/z5pQv6fGoRL1dchyPN3Lkz3eeNsX2KilVKKX11E7ETQQ60nAot6kNxIeTJwDj8clY3fGJZytTbouItEgtY0hZ5EVgP6AtMAmfZPMCPgwpIpIC9XAlXZXq4YqIVJgCroiISAo0pCwiIpICBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAFRERSYECroiISAoUcEVERFKggCsiIpICBVwREZEUKOA2F3X4H9kcWOmGiIhIU1DAbS5WA3cAiyvdkCLtDNwNzMZvHMaVmE9EpMoo4DYXS4HT8O9p3Rq1BxYBPwTmlCGfiEiVqe6AWwdsBg6NrD8PWAjURtafDMwA1uI9sFHE76EReE/0MGA6sA54HxgUyXchHlTWAh/iPbuovfCeXjblGlLOAJcD7wHrgZnAiTH5xgFTgRuBBXhwuy5HmQCd8f3UtpE8ScwELsC/fm91GfKJiFSZ6g647wNPAcMi64cB9wAbQ uGA2OB64E98KB8IXBujrLbA9cA3wG6AscDK0KvDwZ BlwG7AYcgwebqBl4MN0pz7acDvwAuBrYEw9YdwEHxOT9EvA60DNo1xXAITnKvQiYBxyVp34RESmZVXX6NsZijNbB8i4YhnFAJN88jEsj6y7GeDWmzBFBGYMaqfcsjJUYHRK2sy4oc2CO16djjI sex7jrsi6cRhvRta9iTEqR7mjg3qHlnGfvxy0o1z5lJSUlKogVXcPF BPQCfgiGB5GPAW8O9Qnu74sOoY6u eG4DeOcpdD7zUSL0P4sO5b G90QuAHkVtgesDvBxZNx3YPSbvO5HlFXgvPM5ovIf9QAltExGRvKo/4C4DHgZOCJaH4UOxYZng/2ODn8OpY45yV LPh3NZAPTHnwvPxYemXwN2KKz59VhkOROzjhztysSsExGR1FR/wAUPsEPxCUl703Dy0kLgA DwMte7Hp/A9H1gf7yXeXCRZc0B9o2sG0DpM327ALvgz6RFRKTJROfpVqeH8F7f74AXgVkxea7BJ019CNyPz9o9FB9uvrKIOo/De7NPAsuBbwZtmFFEWQRtuxmfBPbPoLxB FB1KUbik7GOpbRh5Vb4zQxAO/zmYgA Q/uNIvKJiFSZlhFw1wL34TN9L8qR5zbgE B7eABaDbyKB7liLMeD4Y ANngwOY6GwX4y8OXQ8gvB///BPzKUNR5/Bvyj4P 5wKnAv4psX7l1wp8pZ 2OB/FZ NB6oflERKpMrqeAIiIiUkYt4xmuiIhIhSngioiIpEABV0REJAUKuCIiIilQwBUREUmBAq6IiEgKFHBFRERSoIArIiKSAgVcERGRFCjgioiIpEABV0REJAUKuCIiIilQwBUREUmBAm5UHf79SQML J05wGVF1jcO/4q lmIC/v3ESRVzPEREmiEF3KjVwB3A4jKVtxgYUaayymkk/r20K/Dv7n0aOCIm3 nAM8DSIP0DODilNkLy49Fc97OISEABN2opcBrwTmWb0eTWATcCxwRpLjAJ Ewk3/HAVOAE/IviPwGmAHuk1M6WcjxEpEWwqk3vYZyV47WbMSaFlvfC6v0bmOP32mCMxViGsQTjaow5GJeF8nSJlBX NzxS3jiMyRhXYXyEsQjjuka2qTNGHUbbMu r1hibMM7Pk28bjM0Y3yuyngnB9t6GsQpjYbDt0XxJjkch xmMC4NjtRbjQ4y7y7wPlZSUlBpJ1d3DfRY4MMdrB JDpVkzgAywU54yrwCGAScDXwjK2SWSZ1lQVgZYAnw3tDwupsyDgO7A4cB1QR2H5Kj/ImAecFSedhaiIz7EnAGez5N3myDfohLqGwysBfYHRgFX4z3psCTHo5D9PBj4Gf6sfTe8Vz zhG0QESlQdQfcZ4ADgp/3AP4AtAfa4kOnz T4vcacDdwE/A34D/7csNS9uAwPeK8BvwTeI/eNQjntCWwEVuKB6CvAc3l 51o8UN1TQr1L8BuHWcCdwF Ac0ooL4nd8OHwR4APgGn4toiIpKT6A25/vFd2LPBV4It4z8qAFwosrwuwPfBKaN08PICUYhawObS8COiaI 9ovAf3QIl1gs uHgAcCjwI/BbYvZH8o4EjgSH4M BizcQDfdarQN8SykviQXy/vgVMBC4AejRxnSIiIdUdcF/DZ EeAHwZGIMPxR4IvIgPaxbCgv83RNZHlwu1MWZdpsQyk1iHD90 BZyB3zhcmiPvtcB3gC/hQasUFllOY1sX4DdfJ MTxM7Fz48dUqhbRIRqD7ibgX/hz  6A78CDsMDcDHDycvxXlKf0LptgrJzWQe0LqKuXLrgz4zbl7HMrBqgQ8z6G/CZwocCb5Shnk8DtaHlvfFefimS7Of1 Izr7 OjHF1J9yNOItKiVXfABQ sZwGP4gFzId7LLSbgAtyCP8ftie 90UCrRvLPwp NdsefHTeWN4mRwNv40G6xWgF/Bk4CPodP1poA7AXcG8n7S3z/nY8H4wFBqiuh/m7Az4F wCnA14GxJZQH ffzcfhz4r3wiVjfxm/IZpRYr4hIQtUfcJ8GOgMPB8uT8Fm5z0byTcaHOucFyy8Ey9EL8o/xXtIM/CK/Dg AuYzCA8y7wBr8D0lU2mZ8otRo4DF80lJ/fKbwfZG8JwCdgvXTQ mqEup/FGgHvIT3nn8I/CmSJ nxyMq3n5fj2/I03ks/EQ/CpfasRUQSytDwiZqIiIiUWfX3cEVERJoBBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAFRERSYECroiISAoUcEVERFKggCsiIpICBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAzZqDf2 SATenWO/QoM6OKdYpIiKpU8DN6oN/WeFjlW5ISkbi32u7Av u2KeBI4rMNxy/aZgSWtcKmB sHxisqw2WR0Z fxx wyMiUsUUcFuqdcCNwDFBmgtMAj5TZL41wF5Az2D5iOB3RUQEaCkBtwcwAViIB4ZpwJAiy8oAlwPvAeuBmcCJZay3N/A2PqydiXm9M1AHtC2w3VG3Bm17Cu 1Dsd7pV8sMt9m4E/AScHyKcDEEtp3GluG MPp4hLKFBGpoOoPuO2BJ4EBeGDcG7geH0IuxunAD4CrgT3xoHIXcEAZ6u2HB7Z7gXPxABN1ETAPOKrI9sfpiA/zZoDnS8j3e BkoBNwJPCXEtr0e6BdKA3Db3CeKqFMEZEKi tHVE86HWMDxi4J8z KcXMjr0/HGB9Z9zzGXUXWOxTDMD6HsRDj 3nyjw7yDy3DvtkTY2NQ3hKMo4vMNxxjVfDzTIwbMf6A0Sf4nYHBa7XBcty/OY20cw MFRhnlWGblZSUlCqUqr Huy/ 3PGdMpXXB3g5sm46sHuJ9T4CbBdTdtRovIf5QMJyGzMH74EfCjwI/JaG21FIPvAe//l4DzWXn H7J5vubyRv5 D1PwK/aSSfiEgzV1vpBjS5DH5vUU7R8uLqKLTei4DdgNuBfYD3i25dcuuAGcHPTwGvAJcCZxaZD2A8sAqfsbxLjno/oP6Nxcc58mXwAL4UH2IXEdmKVX8PdxoeyHZOmH8V/swwlzl4ryxsAA0/1lJovffiz4ZnA3fjE5PidMEDWfuE5RaiBuhQYr4F KzmjWVoz2hgEPB1/PmtiMhWrPoD7j340O59wGH4LOAhwHk58j8HHA3sh88yjgbfsfhM3FOBvsCVeFC4qcR6wYPUiXgA/0GOPCPxWcxHNlJOPq2AP Pb8TngcHwm8l544C80X1P4f/hs8FPxzwB3DFLrJq5XRKQJVfxBcpOnHhgTMD7CWIPxMsZXc TtgHE3xkp8Ms IyOsZjKsw5uGTomZhnFJCvdlJUx1D676FsQnjizFljqb0SVMZjNsxZmN8grEM4zmMbxaZLzxpKpxyTZoaGck3joaTpn5G/OSqi0vYbiUlJaUKpqZ4wikiIiIR1T kLCIi0gwo4IqIiKRAAVdERCQFCrgiIiIpUMAVERFJgQKuiIhIChRwRUREUqCAKyIikgIFXBERkRQo4IqIiKRAAVdERCQFCrgiIiIpUMAVERFJgQJupU0AHiogfx3 /U4Dc7w hy1fBnVzGcorVLnLq5Tmuh0TKOx8EZFmQwF3a7MauANYnOP1PkAGeKxM5WUtBkaUsbzmrlq2o6VJep6KVEBtpRsgBVoKnNaCyquUatkOEWk2WkYPtwc FLcQWANMA4ZE8hwMTAEWAeuA14CTYsqaGOS7E7 bng9cEpMvaXngtz23AauCNl4Vk2cvtgwVl2OoM0l5XUKvdwNuDS0PL6F9JwMzgLXAbGAU8WfihfgQ VrgQ DuRsrsjA8Dt20kTxKFbEeS9hVyHiSV5HwZB0yOrHsRGBOTt5D93JgDgY34yMAS4Grgfvzm5bJI3kL2S772FXKeQvLzbwT Hj8MmB60831gUI52iiRgVZ3aY8zCeBnjcIw GN/AuDCS73iMizEGYvTGOAdjM8bBkXwTMQzjLIwMxv4YKzGGFlneBIyNGL/C6IdxCsa64PfjtqcuqH9gnu1 FOPmBPsnaXmLMUaUobzhGCswTsLYFeMojA8xzo/kG4yxCeM4jF4Y 2Fc3Ui9o4N6o8eh2JRvO5K2L l5kDQlPV/GYUyOrHsRY0yJ 7mxdGCwz47FuCT4 QyM0zBWYdQUsV8KbV  8zTp UdQzicYz2AMwuiAcVCw38txjim1xFTxBjRtOh1jA8YuRfzuSzS8QE3EmBtZdzvGlCLLm4CxEKM2tO5ujKdylLG1B9x5GJdG1l2M8Wpk3Vn4jUyHhMdqNOkG3ELbl 88SJqSni9JA24p2xFN2YDbGmNA8PP2oX3ZvYj9Umj78p2nSc8/gnIMD7blOKeUWnyq/iHlfYG5wDt58nUFfoIPu70PLMCHFzvH5J0ds9y3hPJm4kNxWa/GlFcNuuPDvmOofxreAPSO5H0QH258Cx/GvwB/NJDLaHyy2ANlbXFuSdtXyHmQVDnPl0L3cz6bgA34cC34I5zsz 1C ZLul3K2r5DzL2s98FKR9YlEVH/AzeBvqnzuxp/VXIw/ixoAvEz8HmodWa4N6im2vGj7omVVi x2HRv8HE4dI3kXAP3x521zgXPx53w7pNLS/JK2r5DzIKkk50vcOd8qZl2a znczqT7pZztK T8y1oJbC6iLpEY1R9wpwG7ATs3kqcGOBy4HngCv P mNx3vXtSf373PtTv9RZa3qcj5e0NzGqkvUmson6PolTraHijUaiFwAf4vkliPTAV D6wP94rOjhH3i7ALkD70ppYkHztK/Q8SCrJ bIU6BRpS12O8grZz VQ6H4ppH2NnaeFnn8iZVb9Afce/M74PvyOujc Q/m8UJ7N CzIwfgeaY0PM3XNUWY34BdAP CMoLxbSyzv50F5pwBfB8Ym38RYzwFHA/vhQ3ClBt9ZwFfwYbm2xPeWkrgGn/15Od5zGYAPE14XyXcccA4 zLgT8G18v87IUe5I4G3gyCLbVagk7Sv0PEgqyfnyAh6cPo334EYC2xa5HeVWyH4ptH35ztOk559IE6j gPsJcCg DPVH4D/AtcC7kXzD8J7qB/ibdhXwZI4y/473HqYBPwZ gAf0Yst7FA IL EXnh8Cf4rkmYwPE84Lll8IlnNdeG7Cew9P4h9dOrXE8kbhF/p38edypxdZ3m3B734TH0J8DBiK78uw5cAJwNPAG8CJ MW31J5/Pkm3I2n7CjkPkkpyvtyHfxTuGfyGc1t8f0dVaj8n3S Fti/feZr0/BNpAkmfcErWRPx5z9BKN0RERLYm1d/DFRERaQYUcEVERFKgIWURadwv87w H/9MrYg0SgFXREQkBRpSFhERSYECroiISAoUcEVERFKggCsiIpICBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAFRERSYECblOrAX4DLMH/pte4HPnqgtcHptSuStvat3cO3n4Dbq5wW0Rkq6CA29SOwb L9kj8O0nPy5FvNXAHsDildjWVxfgXfOeztW9vH/wPoz5W5nKT7r9qcAZ 47IO/27awZVtjkhTU8BtarvjX7L9ErAM/1LsOEuB04B3UmlV5bW07ZX6jgbGAxOAQfj7429A3wq2SSQFVvWpB8YEjIUYazCmYQyJ5MlgXI7xHsZ6jJkYJ8aUNQ5jKsaNGAswFmFclyNf3L9xkXx7RV4fmGMbajF hbEMYwnGVRhzMC6LqXdyZN2LGGNiyhyBsRjjMIzpGOsw3scYFMpzMMaUYDvXYbyGcVKknC45ttUwhhe5veU HtnUGaMOo20jeQpJj2Lc3Mjr5d5/YJyMMQNjLcZsjFEYNSXsl3zvj 2Cth8X b1vBMemexH7bTLG46HlWoz5GDeU6bgoKTXPVPEGNG1qjzEL42WMwzH64BeKCyP5zsAvYKdi9MW4Er/gHRDJNw5jI8ZZ EXusCDfITnqvwwPjPnaWUfjAehKjKUYX8P4NMYDGBsoPeB gvEMHmQ7YByE0S U53iMi4N29cY4B2MzHkji2rk4KLfU7W2q4zE6eH1ogjYmSfkCbrn333CMFXjQ3hXjKIwPMc4vcr8kfX/cgzEpsm4Sxp9Dy6eR 8YheqyXYlwTKe9 jKfKdFyUlJpnqngDmjadjgemXfLkm44xPrLueYy7IuvGYbwZWfcm3suIK7dcAXcBHiyyyztibKL0gGvU79EmSS/lKA/KF3Cb6niMJt2AW 79Nw/j0si6izFeLXK/JH1/DMYDeM9guUewfFQoT1eMAY2kdkG 1sExOBdjGB5898f4NR78y3FclJSaYaql2u0LzCX/s8I wO8i66YD 8XkjZa1AuhaRNuS2gbYAZ9YkjUfWFSGstfjz89y6QpcChwO9ABq8clf/y5D3Y1pquMxOkhpKef 647P7h4TpLDVMfnfiSzH7Zek74/HgHeBU4K6T8bnJkwJ5Vka1JHLxuD/TPB/LbASeA f29AmTxtEtnLVP2kqg99bJBHNl t3N eoJ21xdca1t1UjZawkfnuy7gYOAy4GDgQG4IE/jTNnazseccq5/7LbdGzwczh1jMmfZL8kfX8YfgN0erB8Kj7pKVzHqcCGRlL2I2Dr8QmE3YGHgH2A14HtgIUJ2iKylar gDsN2A3YOU  OfjdftiAYH2lLccvROH29cAvUFFLgU6h5Rq8V1SMGrxndj3wBPA 8DHQu5HfWQe0LrK sKY6Hl2AXYD2JZaTtQpol O1cu /hXiv8vBiGppD0vcHwO1B3guAPYLlsL/ixyxX k8o77 BQ0PLtcBBwPMFb4HIVqP6A 49 JDZfXhPozcwhIafhx0LnITfpfcFrsQ/rnBTai1t3E3A Xjbd8f/2MKGmHwvAPsDn8Z7LyPxIcxibMYD3GD8TGkN3EDjw ezgK/gvZe2NN67bkxTHY RwNv456LL4Tn8Iy774TdB4eDbFPvvGvxzupcD/fGbkAuA64psf9L3B8CHwKRgGx4F5kVe/xjvvedK4Y/E3Qh8HrgC2Bu4FeiA/5EYkSpV/QH3E/xO jXgj/hd9rX486iw8cCPgvQ6/qzqVOBfTdy yfhwXfbi9UKwPCOS76fAxCA9F T7EO8Rhd2Hf7bxGfxCui31n/0Wahg 5PcBHgxWAU82kn8U0A3fv2vYMgSZlXR7K3U8CnUT3nt9En ufmrk9XLvv9uCdd/Ej tjwFC8p1qMpO PrPH4jcOEIuvLegQYDpwJvAh8Fg/0s0ssV6QZK QJpzQntfgElROBByrcFmk5RuC96V7A2gq3RWQrU/2zlKvFrsAXgKl4r/YS/Hnt1Eo2SlqMTviz78vxXq6CrUjBqn9IuVq0As7FhyXn4M8Mv0z8x0FEyu33 MfHpuPPkUWkYBpSFhERSYF6uCIiIilQwBUREUmBAq6IiEgKFHBFRERSoIArIiKSAgVcERGRFCjgioiIpEABV0REJAUKuCIiIilQwBUREUmBAq6IiEgKmnfAjX5H6tbmDPyLBtbh3106uMR8zb1eERHJqfkF3JHAFyPrhuFfuL01ORr/GrMJwCD8m1b BvQtMl9zr1dERPKyZpV6Yfwa4y6MDzEexrgGo3OR5U3EmIJxJ8ZijPkYl8TkG4cxFeNGjAUYizCuK6G8yRiPh5Zrg7w3FJkvmzpj1GG0zfF6U9WrpKSkpFRSan493A A64AuQHfgfeDnwIoSyjwCeBbYHjgGuBoYGpPvS8DrQE/geOAK4JAiyzsAeDq0vBF4LlhfTL6si4B5wFE5Xm qekVEpCTNL BehA91XgG8AfwZmAR8rYQy3wZ g99jvBSUeXZMvrlBvs3AP4DZwIFFlNcav2H4CB8OXwrsDywEdigiX1KVqldERPJqfgH3D8CRwCvB8hT8me6zMXkvwntm2XRkjjJnxyzHPat8J7K8AuhaRHmZ4P9aYCXwHrAGaBP5vaT5wkYHv/dAzGtNWa IiJSk QXc aGfbwn 3wAsjsk7AdgrlOKCMniPLqyWLUEnbHPMurh8 cpbDyzDh8QfAvbBh6q3w3uRheZLqlL1iohIXs0v4Ibdkuf1j/Fh52xanSPfnnhQzNqHhr3UQiQp79/AoaHlWuAg4Pki82V1AXYB2ud4vanqFRGRkjTvgFsu3YBfAP3wz54OAW5t4vJuBD6PP4veO3i9A/7st5h8WSPxZ8i5hs bql4RESlZxadKN2maiDEJYwLGavwjP5fH5BuHf1QmvO5FjDFFlgfGmRhvYazDeAXjiBLzgTEawzCGNpKnKepVUlJSUiopZYIfqtdEoCPxHwNqDuWJiEiL0DKGlEVERCpMAVdERCQF1T kLCIi0gyohysiIpICBVwREZEUKOCKiIikQAFXREQkBQq4IiIiKVDAFRERSYECroiISAoUcEVERFKggCsiIpICBVwREZEUKOC2BHOAyyrdCPmvNI9HHf7HWwemVJ I5KSAK W1GBiRYn2/Zsu3TW4E3gV A3RvJuVV2mrgDvy4NCdJ97MBa4DtQut CbxRZHkAZ A3PeuAl4HBJWxH0vJOB54BlgbpH8DBJdYrWx0FXNn6vQfsAewDXAl8HfhjMyqvkpYCpwHvVLYZsZLu59Yku4lLUt7RwHj/Hh29AAAGFklEQVRgAjAIeAn4G9C34NYXVt7xwFTgBOBY4BNgStBeaVFS/9b7FpEmYkzBuBNjMcZ8jEty5B0R5DkMYzrGOoz3MQaF8mQwLsd4D2M9xkyME2PKaoMxFmMZxhKMqzHmYFwWyTcOY3Jk3YsYY2LK7IExAWMhxhqMaRhDQq93wXL G55jmztj1GG0LXE//zrYvvC6S4K6t41s71SMGzEWYCzCuK6E8pKmpMcDjJMxZmCsxZiNMQqjJvR6HcZmjEMjv3decGxqQ v2ihyHgY20Md/xTdq pjhuhnEfxocYrYN1v8R4o8jyJmM8Hlquxd bNxS5XwopL5y2CY7l94rcf0pbZVIPtykdATwLbA8cA1wNDM2Rtz1wDfAdoCt R7wi9PrpwA CMvYEJgJ3AQdEyrkCGAacDHwBOBDYpYRtaA88CQwATgT2Bq4H oTyLMO/6DEDLAG G1oel6Pci4B5wFEltC2X1cH/bSPrvwS8DvTE9 8VwCEllJdE0uMxHBiL79v/3765heZRRHH815gqeKEtSp4sFhWviJGqBX0oKPigBBRELYJaiiilagVFRB/irQg VPEGSr1AIxQhKJRWH3xRQdtKSjUWW221RB9qhaoFtYm4PvxncTvZLzu7yffVfPn/YGlmenL27DnZnTlnZi4E7gMeBNYUZH4EPg76iqwANqFSas4o8v/iCvtS4ptq33Rp5eet6F24dQb0LQM KbT/Bj5n8nuU6pdUfTELUHwOVciZruO4j/pdeW0kY3/U9ybKemPZe9FM/Iop9O0kY0PUt52MoajvZzKeKLQXo5l00wx3JRkTZCxJfO5fwvNUyQ2GZ75xmn4uZjY9ZPSj7Gt3yfPujfr2oiytib7UKzUeY2Q8EvU9RMaXUd/dwcd5trck HFZi/ufydQZbmp8U 2b6bjlVZLV6O8TqjPcVvrmB31ryFhBxmEylobf3dPAL3X0xdfbwbaTGvrP16y8nOG2k29L2q3WisbR k8rzkUbMorsBM4rtBeibHpXoW8MZZ1NuQzYz8yvAQ6iGf57M6DrHJRZTCCfHAJuLpH7IWr/jqoJTfVVkRqPPrSb FmOfT2fA86OZN8FTkPVE1B2uw/Y1sA SItvHfvqUMfPb4V7TVWRqNI3L/zbCxxBa75/AieW6ErxSx19RQaB64ABtNHKzBl6j7cBXc38qN3Lfy9pzBHgnwp9WdSeF/XlP09EcnG7TBfACSV98T3 j4wB16OP7U/Il2WU bcsHqn6qkiNR27DTVRPQH4FtqDNN1vQgDvU0L783lXxrWNfHer4 Q/gdWBt L0m saR//rQTufNof8M4GAkm KXOvpyngJWoeWNfRX6TdfhDLedXMyxU5pLmZz1pvIdmnUX6Q/9Ob hWX1xnWkB5UcjDqNMKacHZTExIyhzOCvRzqNMnmiUsRCtZZ6cqHcqxtGa5Tc0HxzboS81HgfRAHFtot4htBfgcrS2 M40bEyJb137Uqnr55eAG2i9JyFF3zZgeaHdC1wNbI/kUv/uU/WBKgJ3Bfn4WJOZE3jAbSenA uB89FZvQHg1Ya6XgZuB 5EZenH0DGEFyO5V4DVaGNQDypflWWuO4ClwEVoNr8WWFQitwmV1oaBa1BZbwBtmiljD/oo9qHNKmX3Jtzve1Ra62ZS4/EkOvryKHABmkw9ADxTIrsZZetvAF8gnzclNb517GsXY8D7aANiU14ArkKb2S5B7 Mp6MxukVS/pOp7HrgHuD/8f3 4yia5pmvxgNtOPkRZ5AiwDu0yHm6oawPwdLh2A3egwfezSG4dOu83ij7ER9HAFjOM1sU RR WRUxeIwaV8pYDX6EzjV jstiBFnY jCYaB9B61sqEZ tmUuPxGvLVLSgOH6EsdqRE9i8Uv6my2w9QSTQvv 4I7dFILjW dexrJ tpPYlLYSvacb0KTVauRANpXHlK9UuqvtvQt2AYrS/n1 PTeBYz65gNK3Szk43AqbQ BmSMMWZO4QzXGGOM6QAecI0xxpgO4JKyMcYY0wGc4RpjjDEdwAOuMcYY0wE84BpjjDEdwAOuMcYY0wE84BpjjDEd4F8ETkXoIo8U7gAAAABJRU5ErkJggg==[/IMG]

---

### Post by ricciolino on 2023-03-08
> **pqwoerituytrueiwoq said:**
> compare value between  hwinfo in windows and my changing bios settings to see what changed then  adjusting the multiplier/divider

you need to load the module in the kernel to get any sensor data

Can you please clarify to me what are you intending with this sentence ?

---

### Post by TheFu on 2023-03-08
[https://forum.level1techs.com/t/no-z690-chipset-linux-drivers-really/184724](https://forum.level1techs.com/t/no-z690-chipset-linux-drivers-really/184724) from 2022 seems to have some suggestions.

---

### Post by ricciolino on 2023-03-08
> **TheFu said:**
> [https://forum.level1techs.com/t/no-z690-chipset-linux-drivers-really/184724](https://forum.level1techs.com/t/no-z690-chipset-linux-drivers-really/184724) from 2022 seems to have some suggestions.

Thanks for sharing the link. I checked it entirely but I don't think are there present any useful suggestions to address my PC fan problems.

I am also taking the opportunity to share here with you the confirmation of which is my specific chipset to manage all the fan connectors. I just opened my assembled PC for checking it closely with my smartphone camera.
The chipset is the **nuvoton 3961S123GA**.

---

### Post by dragonfly41 on 2023-03-08
From past usage, there is gkrellm .. with plugins.

Launch Synaptic and search gkrellm to view options to install.

Actually just running it now, right click on top panel (in popup display)  then ..   Built In > Sensors > Fans

---

### Post by ricciolino on 2023-03-08
> **dragonfly41 said:**
> From past usage, there is gkrellm .. with plugins.

Launch Synaptic and search gkrellm to view options to install.

Actually just running it now, right click on top panel (in popup display)  then ..   Built In > Sensors > Fans

Thank you @dragonfly41, I will also try your suggested tool.

---

### Post by ricciolino on 2023-03-08
Guys!!! I finally found a solution :)

Continuing searching around I ended up into [this]("https://github.com/lm-sensors/lm-sensors/issues/220") issue in the official GitHub lm-sensors repo page.
Check out my last comment in the thread. I solved by installing [this]("https://github.com/Fred78290/nct6687d") kernel module.
After rebooting my PC, the system fan sensors are correctly read by lm-sensors and so from any other third-party application that make use of it.

---

### Post by pqwoerituytrueiwoq on 2023-03-09
> **ricciolino said:**
> Can you please clarify to me what are you intending with this sentence ?

eg: sudo modprobe nct6687

once you have a module loaded that supports your hardware you can use a config file to make the raw sensor data readable

---

