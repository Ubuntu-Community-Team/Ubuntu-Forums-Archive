---
title: "Want to monitor CPU temp, but sensors-detect gives &quot;No sensors were detected&quot;"
date: 2013-03-23
forum: General Help
---

### Post by msilver on 2013-03-23
I've got a fresh installation of ubuntu 12.10, with all updates.  This is a new HTPC build (ASUS F2 A85-M PRO, AMD A8 5500, Scythe Big Shuriken 2) and I'm not all that familiar with any of the hardware.

I want to monitor my CPU temperature, but can't seem to get the information I need. I can look at temperature information in the BIOS, but when I run sensors at the command line I get:

```
matt@htpc:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)
```

Though it seems possible that temp1 is the CPU, I'm not convinced. Regardless, it seems unlikely that anything is running at 0.0[FONT=arial]°C[/FONT]

When I run sensors-detect, the section about embedded CPU sensors fails to find anything. It looks like this:

```
Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

```

And then after responding "yes" to all remaining choices, I end up with:

```
Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

```

The above link to the Devices page on the lm-sensors site provides a link to the latest version of the sensors-detect script (revision [FONT=arial]6127, which is definitely newer than revision 5984 that I have from apt-get). This script does look for slightly different CPU sensors, but again fails to find anything:

[/FONT]```
Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No
```[FONT=arial]

Continuing, it ultimately does detect one sensor, but that sensor doesn't yet have a driver and doesn't look like it's got anything to do with the CPU:

[/FONT]```
Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton NCT6779D Super IO Sensors' (confidence: 9)
```[FONT=arial]

And after running this new version of sensors-detect, the output of sensors remains the same.  Sorry for all the text, but I figure more information is better.... What next? Any ideas!?

Output of sensors-detect (revision 5984, from apt-get):

[/FONT]```
matt@htpc:~$ sudo sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: System manufacturer System Product Name
# Board: ASUSTeK COMPUTER INC. F2A85-M PRO


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc562
    (logical device B has address 0x290, could be sensors)
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): YES
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus


Next adapter: Radeon i2c bit bus 0x90 (i2c-0)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon i2c bit bus 0x91 (i2c-1)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon i2c bit bus 0x92 (i2c-2)
Do you want to scan it? (YES/no/selectively): YES
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)


Next adapter: Radeon i2c bit bus 0x93 (i2c-3)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon i2c bit bus 0x94 (i2c-4)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon i2c bit bus 0x95 (i2c-5)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon aux bus DP-auxch (i2c-6)
Do you want to scan it? (YES/no/selectively): YES


Next adapter: Radeon aux bus DP-auxch (i2c-7)
Do you want to scan it? (YES/no/selectively): yes


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-8)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)


Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

```[FONT=arial]
Output of sensors-detect (revision 6127, from [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices))

```
matt@htpc:~$ sudo ./sensors-detect 
# sensors-detect revision 6127 (2013-03-17 17:04:55 +0100)
# Board: ASUSTeK COMPUTER INC. F2A85-M PRO


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): YES
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 15h power sensors...                             No

AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): YES
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes

Found `Nuvoton NCT6779D Super IO Sensors'                   Success!
    (address 0x290, driver `to-be-written')
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): YES
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any

ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): YES
Using driver `i2c-piix4' for device 0000:00:14.0: AMD Hudson-2 SMBus


Next adapter: Radeon i2c bit bus 0x90 (i2c-0)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon i2c bit bus 0x91 (i2c-1)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon i2c bit bus 0x92 (i2c-2)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon i2c bit bus 0x93 (i2c-3)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon i2c bit bus 0x94 (i2c-4)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon i2c bit bus 0x95 (i2c-5)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon aux bus DP-auxch (i2c-6)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: Radeon aux bus DP-auxch (i2c-7)

Do you want to scan it? (yes/NO/selectively): yes


Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-8)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)



Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `to-be-written':
  * ISA bus, address 0x290
    Chip `Nuvoton NCT6779D Super IO Sensors' (confidence: 9)


Note: there is no driver for Nuvoton NCT6779D Super IO Sensors yet.
Check [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for updates.


No modules to load, skipping modules configuration.


``` [/FONT]

---

### Post by grahammechanical on 2013-03-23
I have just installed lm-sensors to run a test and this is what I get.

> graham@Seven-Raring:~$ sensors
atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:       +1.17 V  (min =  +0.85 V, max =  +1.60 V)
 +3.3 Voltage:       +3.25 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:         +5.04 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:       +12.41 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      1804 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed: 1328 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed: 2177 RPM  (min =  800 RPM, max = 7200 RPM)
CHASSIS3 FAN Speed:    0 RPM  (min =  800 RPM, max = 7200 RPM)
POWER FAN Speed:       0 RPM  (min =  800 RPM, max = 7200 RPM)
CPU Temperature:     +35.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +32.0°C  (high = +45.0°C, crit = +95.0°C)


coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +78.0°C, crit = +100.0°C)
Core 1:       +45.0°C  (high = +78.0°C, crit = +100.0°C)


You should be getting more than you are getting. I also have installed Psensor. It is in the Ubuntu Software Centre. It puts an indicator in the top panel which will give you a drop down menu with the temperatures and fans speeds. I had this installed before lm-sensors. It may have brought in some libraries that lm-sensors is making use of on my machine.

Regards.

---

### Post by Frogs Hair on 2013-03-23
I have to ask because I don't see it . Did you install lm-sensors? ```
sudo apt-get install lm-sensors 
``````
sudo sensors-detect
```

---

### Post by msilver on 2013-03-23
Thanks for the responses!

> **Frogs Hair said:**
> I have to ask because I don't see it . Did you install lm-sensors?

Yep, lm-sensors is installed. Good to double-check...

> **grahammechanical said:**
> You should be getting more than you are getting. I also have installed Psensor. It is in the Ubuntu Software Centre. It puts an indicator in the top panel which will give you a drop down menu with the temperatures and fans speeds. I had this installed before lm-sensors. It may have brought in some libraries that lm-sensors is making use of on my machine.

I hadn't installed psensor. Looks nice. Once I get this working, I'll definitely use it. Unfortunately, no change in sensor detection (even after reboot, just to be safe). And "temp1" in the output of the sensor command still reads 0.0°C:

```
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +0.0°C  (high = +70.0°C)
                       (crit = +70.0°C, hyst = +69.0°C)
```

Maybe there are settings in the BIOS that need to be modified to enable use of the sensors? Could there be special drivers required for the motherboard and/or processor?? Just grasping at straws, here.

---

### Post by QIII on 2013-03-23
I would look through your BIOS/EFI settings.  lm-sensors is finding your AMD processor, but not reporting a temp -- either lm-sensors isn't working or the mobo is not giving it any information.

---

### Post by zero2xiii on 2013-03-24
Oops never mind...

---

### Post by dabl on 2013-03-24
> Found `Nuvoton NCT6779D Super IO Sensors'                   Success!
    (address 0x290, driver **[color=red]`to-be-written')[/color]**

I think this is the problem.  The thermal sensor(s) on your ASUS F2 A85-M PRO are probably new devices, and Linux drivers have not yet been written.  No driver = no output.  :cry:

---

### Post by msilver on 2013-03-25
I scoured the BIOS but didn't find anything of use.  Speaking of the BIOS, is it possible that installing ubuntu in EFI mode could make a difference with this?

Also, I've discovered that the value reported as "temp1" doesn't actually stick at +0.0°C all the time. Tracking the value with psensors, I was able to observe this value occasionally changing when the system was under load... but rarely over 2.0°C and never over about 10.0°C.

Something's not right.....

> **dabl said:**
> The thermal sensor(s) on your ASUS F2 A85-M PRO are probably new devices, and Linux drivers have not yet been written. No driver = no output. :cry:

Probably a good point. Maybe this could also explain why I'm getting nonsense values on the sensor I have? It's still odd, I think, that other sensors aren't even detected, drivers or not. But I guess I don't really know anything about this.  Nonetheless, maybe I should wait for 13.04... ?

In the spirit of waiting, is there a way to mark this thread as "dormant" or something?

Thanks again. I'll update if I discover anything new in the mean time...

---

