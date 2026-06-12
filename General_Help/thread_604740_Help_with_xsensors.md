---
title: "Help with xsensors"
date: 2007-11-06
forum: General Help
---

### Post by jfarhou on 2007-11-06
Hey all, I've recently installed xsensors because I want to monitor my CPU temperature, but it displays nothing.  I tried doing sudo sensors-detect, and here's what i got:

sudo sensors-detect
# sensors-detect revision 4609 (2007-07-14 09:28:39 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801FB ICH6

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 3c20 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
[B]Trying family `National Semiconductor'...                   Yes
Found `Nat. Semi. PC87591 Super IO'                         
    (but not activated)[/B]
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.


It seems as though National Semiconductor is my best bet, but it is not activated (whatever that means).  Please, can someone tell me what I can do to make xsensors work?  My CPU is a Pentium 4 3.0 ghz.  Thank you!

---

### Post by jfarhou on 2007-11-06
I've scoured the internet for answers, but no luck.  I also tried using the gDesklets monitor, but it didnt work.

---

### Post by MyR on 2008-05-11
in case anyone is still interested:

just need to run
```
sudo sensors-detect
```
then reboot and it will work

as seen in: [http://ubuntuforums.org/showthread.php?t=482140](http://ubuntuforums.org/showthread.php?t=482140)

peace

---

### Post by wpshooter on 2008-05-23
> **MyR said:**
> in case anyone is still interested:

just need to run
```
sudo sensors-detect
```
then reboot and it will work

as seen in: [http://ubuntuforums.org/showthread.php?t=482140](http://ubuntuforums.org/showthread.php?t=482140)

peace

It WON'T if the Ubuntu version you are using is Hardy. 

At least, it won't on my machines !!!

---

### Post by tgalati4 on 2008-05-23
Following the links provided in sensors-detect:

11/11/06 22:04:52 changed by ruik  ¶

    * priority changed from major to minor.
    * status changed from new to closed.
    * version changed from 2.9.2 to kernel.
    * resolution set to wontfix.

Hello,

Sorry this chip has no standard way to access the sensors - this chip is in fact a microcomputer which may or may not share the sensors information with the "main" system. The way how it shows sensors depends on its programming and thus no driver can be developed. Sorry.

Regards Rudolf


----------

You may be out of luck.

A place to find temperatures:

/proc/acpi/thermal_zone/THRM

See if there is anything there that you can use.  This path is from a Dapper Drake machine.  It may be different under Hardy.

---

### Post by wpshooter on 2008-05-23
> **tgalati4 said:**
> Following the links provided in sensors-detect:

11/11/06 22:04:52 changed by ruik  ¶

    * priority changed from major to minor.
    * status changed from new to closed.
    * version changed from 2.9.2 to kernel.
    * resolution set to wontfix.

Hello,

Sorry this chip has no standard way to access the sensors - this chip is in fact a microcomputer which may or may not share the sensors information with the "main" system. The way how it shows sensors depends on its programming and thus no driver can be developed. Sorry.

Regards Rudolf


----------

You may be out of luck.

A place to find temperatures:

/proc/acpi/thermal_zone/THRM

See if there is anything there that you can use.  This path is from a Dapper Drake machine.  It may be different under Hardy.

If "THRM" is supposed to be a file, I don't seem to be able to find it under the Gutsy file system ???

Thanks.

---

### Post by MyR on 2008-05-23
> **wpshooter said:**
> If "THRM" is supposed to be a file, I don't seem to be able to find it under the Gutsy file system ???

Thanks.

I couldn't get this app to work & I gave up.

however, for temperature info you can use
```
acpi -t
```
or
```
acpi -tf
```
for Fahrenheit

hope this helps

peace

---

### Post by wpshooter on 2008-05-24
> **MyR said:**
> I couldn't get this app to work & I gave up.

however, for temperature info you can use
```
acpi -t
```
or
```
acpi -tf
```
for Fahrenheit

hope this helps

peace

Thanks but this does not get me anything !!!

---

### Post by MyR on 2008-05-24
> **wpshooter said:**
> Thanks but this does not get me anything !!!

what does it output when you enter "acpi -t"?

---

