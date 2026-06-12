---
title: "I cannot seem to get lm-sensors to work...."
date: 2008-05-08
forum: General Help
---

### Post by Lord Xeb on 2008-05-08
I have other sensors that do work (they are in the panel) but I want them to work on my gdesklets so I can see everything and free up space in my panel, but when I used the lm-sensors tutorial I get this (and yes, I did everything it said to do, this is only the terminal part, everything else went fine): 
```
root@nathan-laptop:/home/nathan# /etc/init.d/module-init-tools
 * Loading kernel modules...                                                     * Loading manual drivers...                                             [ OK ] 
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sudo modprobe i2c-sensor
FATAL: Module i2c_sensor not found.
root@nathan-laptop:/home/nathan# sudo modprobe i2c-viapro
root@nathan-laptop:/home/nathan# sudo modprobe i2c-isa
root@nathan-laptop:/home/nathan# sudo modprobe it87
FATAL: Error inserting it87 (/lib/modules/2.6.22-14-generic/kernel/drivers/hwmon/it87.ko): No such device
root@nathan-laptop:/home/nathan# sudo depmod -a
root@nathan-laptop:/home/nathan# update-modules
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
root@nathan-laptop:/home/nathan# sensors-detect
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

Next adapter: SMBus I801 adapter at 18e0 (i2c-0)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x44
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              yNo


Next adapter: ISA main adapter (i2c-9191)
Do you want to scan it? (YES/no/selectively): Can't open /dev/i2c-9191

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
Trying family `National Semiconductor'...                   Yes
Found unknown chip with ID 0xf911
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
doc/lm_sensors-FAQ.html or http://www.lm-sensors.org/wiki/FAQ
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
root@nathan-laptop:/home/nathan# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
[/PHP]
```

I have gone through and did it the right order, then after that, I did it in my own order. But I still get the same errors.


Any ideas?

---

### Post by rbmorse on 2008-05-08
I thought I had something, but on rereading the OP I need to think about this some more.

---

### Post by skymera on 2008-05-08
What computer is yours? Is it a Dell?

---

