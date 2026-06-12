---
title: "High Cpu usage in Ubuntu 8.04"
date: 2008-05-22
forum: General Help
---

### Post by f.a.b on 2008-05-22
Hi, 
I've just installed Ubuntu v8.04 on my Dell Laptop. Its an Intel Centrino Core 2 Duo T9300 2.5Ghz processor machine with 4 Gig ram. I am running Dual boot with vista ultimate using the grub bootmananger. 
I love Ubuntu!
My problem is that the fan of the computer is constantly worjking and that both processors are always on 10 - 20 % usage when I am doing absolutely nothing. I start Ubuntu / Gnome Desktop (version 2.22.1) and the system monitor and both CPU's are working hard. If I check the processes, they are all at 0% CPU) Any ideas on how to fix that?

---

### Post by tamoneya on 2008-05-22
post the results of typing ```
top
``` in terminal

---

### Post by f.a.b on 2008-05-22
top - 13:02:01 up 9 min,  2 users,  load average: 1.05, 0.60, 0.30
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s): 15.7%us,  1.9%sy,  0.0%ni, 82.4%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3630620k total,   492764k used,  3137856k free,    13244k buffers
Swap:   497972k total,        0k used,   497972k free,   263292k cached
PID to kill: 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5663 root      20   0  822m  30m 7880 S   20  0.8   1:35.70 Xorg                                                                                            
 6262 fconrad   20   0 39888  19m  12m S   14  0.5   0:58.60 gnome-system-mo                                                                                 
 6100 fconrad   20   0 52608  30m  10m S    3  0.9   0:23.50 compiz.real                                                                                     
 6031 fconrad   20   0 36392  19m  12m S    1  0.6   0:01.28 gnome-panel                                                                                     
 6449 fconrad   20   0 75188  20m  11m S    1  0.6   0:01.04 gnome-terminal                                                                                  
 6590 fconrad   20   0  2308 1124  856 R    1  0.0   0:00.16 top                                                                                             
    1 root      20   0  2844 1688  544 S    0  0.0   0:01.16 init                                                                                            
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                        
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                     
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                     
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                      
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1

---

### Post by f.a.b on 2008-05-22
goes down to this when I quit the system monitor:

top - 13:05:18 up 12 min,  2 users,  load average: 0.31, 0.50, 0.31
Tasks: 121 total,   1 running, 120 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.1%us,  1.3%sy,  0.0%ni, 94.9%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   3630620k total,   522828k used,  3107792k free,    13728k buffers
Swap:   497972k total,        0k used,   497972k free,   265624k cached
PID to kill: 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                         
 5663 root      20   0  822m  30m 7860 S    2  0.9   2:19.98 Xorg                                                                                            
 6100 fconrad   20   0 51604  30m  10m S    2  0.9   0:38.99 compiz.real                                                                                     
 6449 fconrad   20   0 75188  20m  11m S    1  0.6   0:01.32 gnome-terminal                                                                                  
 6590 fconrad   20   0  2308 1124  856 R    1  0.0   0:00.38 top                                                                                             
 5237 root      20   0 21088 2196 1888 S    0  0.1   0:00.13 NetworkManager                                                                                  
    1 root      20   0  2844 1688  544 S    0  0.0   0:01.16 init       

However, the fan is always noisier than it would be in Vista.
thanks for help, if there is any.

---

### Post by tamoneya on 2008-05-22
can you install lmsensors or something so that we can look at the temperatures.  It seems like ubuntu is reading them wrong or something.  Also try using gkrellm or conky and you should be able to find the temperatures.

---

### Post by f.a.b on 2008-05-23
Hi,
I've tried all of those tools but don't seem to be able to get much info on fan speed and CPU temperature. lm-sensors sensors-detect comes up with:
# sensors-detect revision 5016 (2007-11-11 22:20:16 +0100)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): y
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel 82801H ICH8

We will now try to load each adapter module in turn.
Load `i2c-i801' (say NO if built into your kernel)? (YES/no): y
Module loaded successfully.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

To continue, we need module `i2c-dev' to be loaded.
Do you want to load `i2c-dev' now? (YES/no): y
Module loaded successfully.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: NVIDIA i2c adapter  (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: NVIDIA i2c adapter  (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: SMBus I801 adapter at 10c0 (i2c-3)
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
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     Yes
Found unknown chip with ID 0x3201
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Trying family `ITE'...                                      No

Some CPUs or memory controllers may also contain embedded sensors.
Do you want to scan for them? (YES/no): y
AMD K8 thermal sensors...                                   No
AMD K10 thermal sensors...                                  No
Intel Core family thermal sensor...                         No
Intel AMB FB-DIMM thermal sensor...                         No

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

sorry for the long file!
Conky is great but does not display temperature info, however, the CPU speed displayed goes down to 800 MhZ if I don't do anything.
Thanks heaps for help!

---

