---
title: "Trying to get fan control working, but sensors aren't being detected"
date: 2014-08-07
forum: General Help
---

### Post by mendhak on 2014-08-07
I'm using an Asus Sabertooth Z97 motherboard.  I'd like to get pwmconfig working so I can control the fans.

Running pwmconfig tells me

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```

Running sensors-detect only finds coretemp, nothing else.

```

# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: ASUS All Series
# Board: ASUSTeK COMPUTER INC. SABERTOOTH Z97 MARK 1


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): 
Module cpuid loaded successfully.
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
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xc803
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
interfaces? (YES/no): 
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): 
Found unknown SMBus adapter 8086:8ca2 at 0000:00:1f.3.
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.


Next adapter: NVIDIA i2c adapter 0 at 1:00.0 (i2c-0)
Do you want to scan it? (yes/NO/selectively): yes
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Analog Devices ADT7481'...                     No


Next adapter: NVIDIA i2c adapter 1 at 1:00.0 (i2c-1)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: NVIDIA i2c adapter 2 at 1:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: NVIDIA i2c adapter 6 at 1:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: NVIDIA i2c adapter 7 at 1:00.0 (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes


Next adapter: NVIDIA i2c adapter 8 at 1:00.0 (i2c-5)
Do you want to scan it? (yes/NO/selectively): yes
Client found at address 0x4a
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Client found at address 0x4b
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                No
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              No
Probing for `NXP/Philips SA56004'...                        No
Probing for `Analog Devices ADT7481'...                     No


Next adapter: NVIDIA i2c adapter 11 at 1:00.0 (i2c-6)
Do you want to scan it? (yes/NO/selectively): yes
Adapter cannot be probed, skipping.
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 


Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)


To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!


Do you want to add these lines automatically to /etc/modules? (yes/NO)
```


I tried searching a bit but my knowledge in this area is limited. 

I found [this thread]("http://ubuntuforums.org/showthread.php?t=1877114") and a few others, so I went into /etc/default/grub and set

```
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
```

Then I did an update-grub and rebooted.  After a reboot, running "sensors-detect" still did nothing extra. I tried 

```
modprobe it87
``` 

But got "modprobe: ERROR: could not insert 'it87': No such device"

I've undone the change since then, but I don't know what 'chipset' I should be loading in its place. If that's the solution.   How can I find out if I'm using an it87 or something else?

I've also seen another thread where [users make it87]("http://crunchbang.org/forums/viewtopic.php?id=21754"), but that scared me off.

I also wonder if the fan controls aren't working due to this being a relatively new motherboard.  

Any troubleshooting tips or links would help.

---

### Post by JKyleOKC on 2014-08-19
I'm searching for help on a similar problem and just posted on a 3-month-old thread, but may be able to help you a bit in this one -- or at least let you know you're not being totally ignored.

The sensors-detect result shows the driver's name as "coretemp" so that would be the one to be certain gets loaded. Search the /etc/modules file for that name. You might then try ```
sudo modprobe coretemp force=1
sensors

```I would expect this to force the driver into place and then report what it senses, but I've not tested it and don't really know whether there's any danger from forcing it into the kernel...

Hope this helps!

---

### Post by mendhak on 2014-08-29
Ah I should have mentioned, I did put coretemp into /etc/modules as suggested by sensors-detect.  That is what (probably) gives me the temperatures in the output.  Just no fan control. What thread were you looking at?

---

### Post by JKyleOKC on 2014-08-29
This is the main one: [http://ubuntuforums.org/showthread.php?t=2239648](http://ubuntuforums.org/showthread.php?t=2239648)
This is another: [http://ubuntuforums.org/showthread.php?t=2222109](http://ubuntuforums.org/showthread.php?t=2222109)

---

### Post by thesuperkid on 2015-01-01
In case you still haven't resolved your issue, I resolved my Z97 problem by doing a `sudo modprobe nct6775` to test, then adding nct6775 to /etc/modules.

The sensors-detect script included in the distro for 14.10 seems to be out of date, but the updated one from [http://dl.lm-sensors.org/lm-sensors/files/sensors-detect](http://dl.lm-sensors.org/lm-sensors/files/sensors-detect) found what I needed.

---

