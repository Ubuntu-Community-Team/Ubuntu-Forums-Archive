---
title: "Conky fan state problem"
date: 2008-05-22
forum: General Help
---

### Post by chunchengch on 2008-05-22
I am using ASUS F3Jc laptop, I have tried many measures to display fan state in conky, but no success, many thanks for reply.

here are all the procedures I ever took, none worked:

1. modify /usr/src/linux-headers-2.6.24-16-generic/.config to change [COLOR="Red"]CONFIG_ACPI_FAN=**m**[/COLOR] to [COLOR="Red"]CONFIG_ACPI_FAN=**y**[/COLOR]

2. add module [COLOR="Red"]fan[/COLOR] to /etc/modules

3. install package lm-sensors and than add the following text in conkyrc

[COLOR="Green"]Fan: $alignr${execi 300 /usr/bin/sensors | grep fan | cut -c11-18}
[/COLOR]
4. use [COLOR="Red"]hwmon[/COLOR] variable, but I can not find anything in /sys/class/hwmon/


here is the text in conkyrc for now
[COLOR="Green"]${color grey}Fan Speed:$color $acpifan[/COLOR]

and its output
[COLOR="Green"]Fan Speed:no fans?[/COLOR]

---

### Post by ram32 on 2008-05-24
Maybe your fan have not sensors?

---

### Post by jjgomera on 2008-05-29
when you proved lm-sensors, did you use command **sudo sensors-detect** to configure it?

---

### Post by chunchengch on 2008-05-29
Yes, here is the output
[COLOR="Green"]
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100) 

This program will help you determine which kernel modules you need 
to load to use lm_sensors most effectively. It is generally safe 
and recommended to accept the default answers to all questions, 
unless you know what you're doing. 

We can start with probing for (PCI) I2C or SMBus adapters. 
Do you want to probe now? (YES/no): YES 
Probing for PCI bus adapters... 
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7 

We will now try to load each adapter module in turn. 
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): 
Module loaded successfully. 
If you have undetectable or unsupported adapters, you can have them 
scanned by manually loading the modules before running this script. 

To continue, we need module `i2c-dev' to be loaded. 
Do you want to load `i2c-dev' now? (YES/no): 
Module loaded successfully. 

We are now going to do the I2C/SMBus adapter probings. Some chips may 
be double detected; we choose the one with the highest confidence 
value in that case. 
If you found that the adapter hung after probing a certain address, 
you can specify that address to remain unprobed. 

Next adapter: NVIDIA i2c adapter (i2c-0) 
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter (i2c-1) 
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter (i2c-2) 
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x50 
Probing for `Analog Devices ADM1033'... No 
Probing for `Analog Devices ADM1034'... No 
Probing for `SPD EEPROM'... No 
Probing for `EDID EEPROM'... Yes 
(confidence 8, not a hardware monitoring chip) 

Next adapter: SMBus I801 adapter at 0400 (i2c-3) 
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x44 
Probing for `Maxim MAX6633/MAX6634/MAX6635'... No 
Client found at address 0x50 
Probing for `Analog Devices ADM1033'... No 
Probing for `Analog Devices ADM1034'... No 
Probing for `SPD EEPROM'... Yes 
(confidence 8, not a hardware monitoring chip) 
Probing for `EDID EEPROM'... No 
Client found at address 0x52 
Probing for `Analog Devices ADM1033'... No 
Probing for `Analog Devices ADM1034'... No 
Probing for `SPD EEPROM'... Yes 
(confidence 8, not a hardware monitoring chip) 
Probing for `EDID EEPROM'... No 

Some chips are also accessible through the ISA I/O ports. We have to 
write to arbitrary I/O ports to probe them. This is usually safe though. 
Yes, you do have ISA I/O ports even if you do not have any ISA slots! 
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290... No 
Probing for `National Semiconductor LM78-J' at 0x290... No 
Probing for `National Semiconductor LM79' at 0x290... No 
Probing for `Winbond W83781D' at 0x290... No 
Probing for `Winbond W83782D' at 0x290... No 
Probing for `Silicon Integrated Systems SIS5595'... No 
Probing for `VIA VT82C686 Integrated Sensors'... No 
Probing for `VIA VT8231 Integrated Sensors'... No 
Probing for `IPMI BMC KCS' at 0xca0... No 
Probing for `IPMI BMC SMIC' at 0xca8... No 

Some Super I/O chips may also contain sensors. We have to write to 
standard I/O ports to probe them. This is usually safe. 
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f 
Trying family `National Semiconductor'... No 
Trying family `SMSC'... No 
Trying family `VIA/Winbond/Fintek'... No 
Trying family `ITE'... No 
Probing for Super-I/O at 0x4e/0x4f 
Trying family `National Semiconductor'... No 
Trying family `SMSC'... No 
Trying family `VIA/Winbond/Fintek'... No 
Trying family `ITE'... No 

Some CPUs or memory controllers may also contain embedded sensors. 
Do you want to scan for them? (YES/no): 
AMD K8 thermal sensors... No 
AMD K10 thermal sensors... No 
Intel Core family thermal sensor... Success! 
(driver `coretemp') 
Intel AMB FB-DIMM thermal sensor... No 

Now follows a summary of the probes I have just done. 
Just press ENTER to continue: 

Driver `coretemp' (should be inserted): 
Detects correctly: 
* Chip `Intel Core family thermal sensor' (confidence: 9) 

I will now generate the commands needed to load the required modules. 
Just press ENTER to continue: 

To load everything that is needed, add this to /etc/modules: 

#----cut here---- 
# Chip drivers 
coretemp 
#----cut here---- 

Do you want to add these lines automatically? (yes/NO)yes[/COLOR]

---

### Post by jjgomera on 2008-05-29
it doesnt recognize any fan sensors  :( 

Check if really it has add that module to /etc/modules, and when you boot again prove command **sensors** to see what sensors you have.

I dont know other functions to that.

---

