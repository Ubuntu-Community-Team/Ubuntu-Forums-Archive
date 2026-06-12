---
title: "Amd Ryzen 1700X no cpu temp problem"
date: 2017-08-22
forum: General Help
---

### Post by fenikstak on 2017-08-22
Hello. I need cpu temps but they are not showing, It only show cpu usage.

I have downloaded Psensor and lm sensors and I type in termial
> Sudo sensors-detect
then I type "Yes" to all question.

Here is that thing from terminal:

```
# sensors-detect revision 6284 (2015-05-31 14:00:33 +0200)
# System: Micro-Star International Co., Ltd MS-7A34 [1.0]
# Board: Micro-Star International Co., Ltd B350 TOMAHAWK (MS-7A34)
# Kernel: 4.10.0-32-generic x86_64
# Processor: AMD Ryzen 7 1700X Eight-Core Processor (23/1/1)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): yes
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           No
AMD Family 16h thermal sensors...                           No
AMD Family 15h power sensors...                             No
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
Intel 5500/5520/X58 thermal sensor...                       No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found unknown chip with ID 0xd352

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): yes
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): yes
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): yes
Found unknown SMBus adapter 1022:790b at 0000:00:14.0.
Sorry, no supported PCI bus adapters found.

Next adapter: SMBus PIIX4 adapter port 0 at 0b00 (i2c-0)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x1c
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `Atmel AT30TS00'...                             No
yClient found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
eClient found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: SMBus PIIX4 adapter port 2 at 0b00 (i2c-1)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x1c
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `Atmel AT30TS00'...                             No
yClient found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 eNo
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: SMBus PIIX4 adapter port 3 at 0b00 (i2c-2)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x1c
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `Atmel AT30TS00'...                             No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: SMBus PIIX4 adapter port 4 at 0b00 (i2c-3)
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x1c
Probing for `Texas Instruments TMP421'...                   No
Probing for `Texas Instruments TMP441'...                   No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `ST STTS2002'...                                No
Probing for `ST STTS3000'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `IDT TSE2004'...                                No
Probing for `IDT TS3001'...                                 No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP9804'...                          No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP98244'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Probing for `Atmel AT30TS00'...                             No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No

Next adapter: NVIDIA i2c adapter 1 at 23:00.0 (i2c-4)
Do you want to scan it? (yes/NO/selectively): yes
Client found at address 0x48
Probing for `National Semiconductor LM75'...                No
Probing for `National Semiconductor LM75A'...               No
Probing for `Dallas Semiconductor DS75'...                  No
Probing for `National Semiconductor LM77'...                No
Probing for `Analog Devices ADT7410/ADT7420'...             No
Probing for `Analog Devices ADT7411'...                     No
Probing for `Maxim MAX6642'...                              No
Probing for `Texas Instruments TMP435'...                   No
Probing for `National Semiconductor LM73'...                No
Probing for `National Semiconductor LM92'...                No
Probing for `National Semiconductor LM76'...                Success!
    (confidence 2, driver `lm92')
Probing for `Maxim MAX6633/MAX6634/MAX6635'...              Success!
    (confidence 2, driver `lm92')
Probing for `NXP/Philips SA56004'...                        No
Probing for `SMSC EMC1023'...                               No
Probing for `SMSC EMC1043'...                               No
Probing for `SMSC EMC1053'...                               No
Probing for `SMSC EMC1063'...                               No

Next adapter: NVIDIA i2c adapter 2 at 23:00.0 (i2c-5)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: NVIDIA i2c adapter 4 at 23:00.0 (i2c-6)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: NVIDIA i2c adapter 6 at 23:00.0 (i2c-7)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: NVIDIA i2c adapter 7 at 23:00.0 (i2c-8)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: NVIDIA i2c adapter 8 at 23:00.0 (i2c-9)
Do you want to scan it? (yes/NO/selectively): yes

Next adapter: NVIDIA i2c adapter 9 at 23:00.0 (i2c-10)
Do you want to scan it? (yes/NO/selectively): yes


Now follows a summary of the probes I have just done.
Just press ENTER to continue:    

Driver `lm92':
  * Bus `NVIDIA i2c adapter 1 at 23:00.0'
    Busdriver `nvidia', I2C address 0x48
    Chip `National Semiconductor LM76' (confidence: 2)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
lm92
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)yes
Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.

Unloading cpuid... OK
```

---

### Post by QIII on 2017-08-22
Hello!  Did you run the command at the end of tbe output?  If not, do so and try again.  If you still don't see it, reboot.

Please post the results of sensors if you still have an issue.

---

### Post by fenikstak on 2017-08-22
Sorry. but what command?
I'm new to linux and ubuntu.

---

### Post by QIII on 2017-08-22
This:

```
Monitoring programs won't work until the needed modules are
loaded. You may want to run '/etc/init.d/kmod start'
to load them.
```

So run 

```
sudo /etc/init.d/kmod start
```

However, it does not appear to be certain that the temp sensor was detected on your Ryzen.

---

### Post by fenikstak on 2017-08-22
Still nothing, 
[by the way I'm on ubuntu 16.04 LTS]

---

### Post by QIII on 2017-08-22
OK.  Reboot and check again.  Please post the output of 

```
sensors
```

when you have rebooted.

---

