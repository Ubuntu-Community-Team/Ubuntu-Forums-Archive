---
title: "Monitoring CPU temp(s) - Is it worth it?"
date: 2014-02-26
forum: General Help
---

### Post by freebird54 on 2014-02-26
I recently built myself a new machine - and am slowly setting it up to take over as my 'go to' box.  I recently (with much assistance from **vindsl** and **paramvir**) made a strong start on a Conky setup that does most of what I wanted for keeping an eye on my system - but have yet to add in CPU temperature monitoring.

Research suggested that *acpi -t* or *lm-sensors* were the most likely source of the needed input, but this has been unsuccessful in practice. Trying *sensor-detect* failed to find anything, and *acpi -t* gives no information at all (no terminal output).

Digging deeper I located a 'newer' version of sensor-detect, which informs me that I need a driver (**nct6775**) not found on my system.  On accessing that driver I find that it appears to need to be compiled into the kernel. So - I am left with several questions, and uninformed speculation :)

1. Is this correct - must it be compiled in to be usable?

2. If it must be, will the changes to the kernel between 2.6.33.5 (the version the driver was apparently developed for) and the 3.8.0.35 I am running now cause any problems?

3. Apparently it was 'upstreamed' - but has as yet not made it into our kernel.  Is it likely to appear (or DOES it appear!)  in the 3.14.x.xx or whatever is coming in Trusty? Will I need to nothing but wait?

4. If I don't wait, does it mean (as seems logical) that I would need to recompile the kernel for each received update until (if ever) this driver makes it in?

5. How easy **is** it to compile a kernel?  And - how likely am I to bork the system trying?  Is it 'safer' to access the kernel from another distro on the same machine for changes, then rebooting to the new result?  Should I leave it alone? :)

6.  Is there some other way to get this done?

I hope this is the right place to ask these questions - if not I hope a moderator can relocate appropriately!  Thanks in advance to anyone who can answer any of the above....or steer me in a better direction!

---

### Post by TheFu on 2014-02-27
TL;DR - skimmed a few parts, but definitely didn't read the entire post.

I don't bother monitoring CPU temps. Why not?
* all modern CPUs have thermal protection built-in; they will protect themselves. I've never seen that protection used.
* No overclocking here.
* Use thermal grease properly during system builds
The BIOS shows CPU temps and whenever I've looked (like yesterday), the machines are usually 20 degC below where the thermal alarm alarms are in the BIOS.

Rebuilding a kernel is something everyone should do a few times. In the 1990s, I built kernels all-the-time. These days I avoid it and any software or driver that requires rebuilding will not be purchased. It simply isn't worth my time anymore.

So ... if you can't get the CPU temps - I wouldn't bother.  Actually, I haven't bothered.

---

### Post by freebird54 on 2014-02-27
Thanks for the input.  I agree that one must do a compile SOMETIME - but in my case it hasn't been since 1993 that I attempted such a thing.  I had to add ATI support to TAMU (Texas A&M University version of Linux) so as to run Motif in glorious colour!  Come to think of it - the result was quite a *fast* machine - that 386 - I set up a couple of incoming phone lines and 3 of us were using it for compiling and testing code from our 'C' course!

Still hoping that someone might let me know if it can be achieved, because this machine has frequently shut down - probably, but not certainly, due to the thermal protection you mention.  I have it relocated now, and apparently running much cooler - but knowing the problem was approaching would still be useful.  I lost a few things from being 'in' the files when shutdown occurred, and you can't check if it was heat-related when it IS shutdown :)  - so I would prefer to get the monitoring to work!

On with the research...

---

### Post by Yellow Pasque on 2014-02-28
Rather than asking if it's doable, it would have been much faster for you to actually try to do it...
```
cd ~/
git clone https://github.com/groeck/nct6775.git
cd nct6775
make
sudo make install
sudo depmod -a
sudo modprobe -v nct6775
```

---

### Post by freebird54 on 2014-02-28
I would be happy to 'just do it' - but I still suspect there is a bit more to it than that.  For one thing, I don't have a programming environment set up on this system - and unless it has changed, it is not in place by default. Perhaps I just asked my questions in the wrong area, as I would still prefer to have them answered before diving in - especially if it is likely to appear (or HAS appeared) in later kernels.  After all, my expertise **was** in 680x0 assembly, not C++ on Intel style systems...

How does one get a moderator to move a thread?  I didn't study the contents here before posting - and I guess I should have :redface:

Thanks anyway.

---

### Post by Yellow Pasque on 2014-02-28
You're making it too difficult... Programming environment? If you have the build-essential package and the linux-headers package corresponding to your kernel, that's all you should need. (If it works, then you'll want to use dkms to install it so you don't have to manually rebuild every time the kernel is updated.)

Just for clarity, I'll attempt to answer your questions
> 1. Is this correct - must it be compiled in to be usable?
If it's not built into the kernel, then yes.

> 2. If it must be, will the changes to the kernel between 2.6.33.5 (the version the driver was apparently developed for) and the 3.8.0.35 I am running now cause any problems?
Nothing's guaranteed, but I highly doubt it.

> 3. Apparently it was 'upstreamed' - but has as yet not made it into our kernel. Is it likely to appear in the 3.14.x.xx or whatever is coming in Trusty? Will I need to nothing but wait

You don't tell us exactly what chip you have (the nct6775 module supports a few). According to the lm-sensors wiki, kernel >= 3.12 supports them all. [http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

> 4. If I don't wait, does it mean (as seems logical) that I would need to recompile the kernel for each received update until (if ever) this driver makes it in?
5. How easy is it to compile a kernel? And - how likely am I to bork the system trying? Is it 'safer' to access the kernel from another distro on the same machine for changes, then rebooting to the new result? Should I leave it alone? 
Again, use dkms if you want the module automatically rebuilt for newer/updated kernels. You don't have to compile the whole kernel either, just the module (it literally took about 2 seconds on my modest system).

> 6. Is there some other way to get this done?
Either build the module yourself or get a newer kernel where it's built in. Those are your options.

---

### Post by Elfy on 2014-02-28
*Thread moved to **General Help**.*

---

### Post by freebird54 on 2014-02-28
Thanks Temüjin - that answers everything I needed to make a sensible choice (for me).  Given time to try it, will probably try the compile - but in the meantime I can pop Trusty on another partition and try there - and if it works I can put off the compile :)

I gather that if you compile the module correctly for the version, then you can bind it in to subsequent updates - so that clears up the confusion about whether you needed to compile the whole kernel, or just find a bindable module somewhere.  Time I learned that!

Thanks again.

---

### Post by ivan54 on 2014-09-29
```
# sensors-detect revision 6170 (2013-05-20 21:25:22 +0200)
# System: MSI MS-7640 [3.0]
# Board: MSI 990FXA-GD65 (MS-7640)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595...                       No
VIA VT82C686 Integrated Sensors...                          No
VIA VT8231 Integrated Sensors...                            No
AMD K8 thermal sensors...                                   No
AMD Family 10h thermal sensors...                           No
AMD Family 11h thermal sensors...                           No
AMD Family 12h and 14h thermal sensors...                   No
AMD Family 15h thermal sensors...                           Success!
    (driver `k10temp')
AMD Family 15h power sensors...                             Success!
    (driver `fam15h_power')
AMD Family 16h power sensors...                             No
Intel digital thermal sensor...                             No
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No

Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               Yes
Found `Fintek F71889A Super IO Sensors'                     Success!
    (address 0x480, driver `f71882fg')

Some systems (mainly servers) implement IPMI, a set of common interfaces
through which system health data may be retrieved, amongst other things.
We first try to get the information from SMBIOS. If we don't find it
there, we have to read from arbitrary I/O ports to probe for such
interfaces. This is normally safe. Do you want to scan for IPMI
interfaces? (YES/no): Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (yes/NO): Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No

Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): Using driver `i2c-piix4' for device 0000:00:14.0: ATI Technologies Inc SB600/SB700/SB800 SMBus
Module i2c-dev loaded successfully.

Next adapter: SMBus PIIX4 adapter at 0b00 (i2c-0)
Do you want to scan it? (yes/NO/selectively): Client found at address 0x50
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

Next adapter: SMBus PIIX4 adapter at 0b20 (i2c-1)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 0 at 1:00.0 (i2c-2)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 1 at 1:00.0 (i2c-3)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 2 at 1:00.0 (i2c-4)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 6 at 1:00.0 (i2c-5)
Do you want to scan it? (yes/NO/selectively): Client found at address 0x4a
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

Next adapter: NVIDIA i2c adapter 7 at 1:00.0 (i2c-6)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 8 at 1:00.0 (i2c-7)
Do you want to scan it? (yes/NO/selectively): 
Next adapter: NVIDIA i2c adapter 11 at 1:00.0 (i2c-8)
Do you want to scan it? (yes/NO/selectively): Adapter cannot be probed, skipping.
Now follows a summary of the probes I have just done.
Just press ENTER to continue: 
Driver `k10temp' (autoloaded):
  * Chip `AMD Family 15h thermal sensors' (confidence: 9)

Driver `fam15h_power' (autoloaded):
  * Chip `AMD Family 15h power sensors' (confidence: 9)

Driver `f71882fg':
  * ISA bus, address 0x480
    Chip `Fintek F71889A Super IO Sensors' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
f71882fg
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!

Do you want to add these lines automatically to /etc/modules? (yes/NO)Successful!

Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK

```

and after that i type sensors

```
koiv@koiv:~$ sensors
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +5.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       77.56 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +1.11 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.31 V  
Vbat:         +3.28 V  
fan1:        2400 RPM
fan2:           0 RPM  ALARM
fan3:        1236 RPM
temp1:        +36.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +46.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +32.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor
```

how to know cpu core temp?
It should display something like:```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0C  (high = +76.0C, crit = +100.0C)

 coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0C  (high = +76.0C, crit = +100.0C)

 … 


```
System Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI 990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB, Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D, Graphics: MSI NVIDIA GeForce GTX 760 2048MB (540/3004MHz), Audio: Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411

Software:
OS: Ubuntu 14.04, Kernel: 3.13.0-36-generic (x86_64), Desktop: Unity 7.2.2, Display Server: X Server 1.15.1, Display Driver: NVIDIA 331.38, Compiler: GCC 4.8.2, File-System: ext4, Screen Resolution: 1920x1080

---

### Post by CantankRus on 2014-09-29
Install inxi and compare.
Not foolproof but helps.

```
sudo apt-get install inxi
```

then run
```
sensors && inxi -s
```

Should see similar to pic.
Last 2 lines shows inxi output.

---

### Post by ivan54 on 2014-09-29
> **CantankRus said:**
> Install inxi and compare.
Not foolproof but helps.

```
sudo apt-get install inxi
```

then run
```
sensors && inxi -s
```

Should see similar to pic.
Last 2 lines shows inxi output.


this output :

```
koiv@koiv:~$ sensors && inxi -s
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +4.8°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       93.71 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.31 V  
in1:          +0.92 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.31 V  
Vbat:         +3.28 V  
fan1:        2392 RPM
fan2:           0 RPM  ALARM
fan3:        1240 RPM
temp1:        +35.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +43.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +31.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

Sensors:   System Temperatures: cpu: 35.0C mobo: 43.0C gpu: 31C 
           Fan Speeds (in rpm): cpu: 2392 fan-2: 0 fan-3: 1240

```

how to know cpu core temp?
It should display something like:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +46.0C  (high = +76.0C, crit = +100.0C)

 coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +44.0C  (high = +76.0C, crit = +100.0C)

 …                       

     
 

```

---

### Post by CantankRus on 2014-09-29
What you see with sensors depends on your hardware and what drivers have 
been written. See [**_[COLOR="#B22222"]lm-sensors.org[/COLOR]_**]("http://www.lm-sensors.org/")

---

### Post by ivan54 on 2014-09-29
> **CantankRus said:**
> What you see with sensors depends on your hardware and what drivers have 
been written. See [**_[COLOR=#B22222]lm-sensors.org[/COLOR]_**]("http://www.lm-sensors.org/")

thx for fast respond and i want ask again if hardware doest list in lm-sensors? how to read the relsult 

[http://ubuntuguide.net/monitor-cpunvdia-gpushard-disk-temperature-in-ubuntu-using-psensor ]("http://ubuntuguide.net/monitor-cpunvdia-gpushard-disk-temperature-in-ubuntu-using-psensor")

"Motherboard: MSI  990FXA-GD65 (MS-7640) v3.0" 
System Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI   990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB,   Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D,   Graphics: MSI NVIDIA GeForce GTX 760 2048MB (540/3004MHz), Audio:   Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411

Software:
OS: Ubuntu 14.04, Kernel: 3.13.0-36-generic (x86_64), Desktop: Unity   7.2.2, Display Server: X Server 1.15.1, Display Driver: NVIDIA 331.38,   Compiler: GCC 4.8.2, File-System: ext4, Screen Resolution: 1920x1080

---

### Post by CantankRus on 2014-09-29
It's hard to know exactly what temperature the sensors output represents.
For me the purpose of sensors is to monitor my cpu temps and fans.
For the cpu temp I choose one that looks about right then run a cpu intensive application (eg youtube vid)
and if the temp fluctuates with cpu activity I'm happy to use it.
Have a look at the lm-sensors link in previous post.

---

### Post by ivan54 on 2014-09-29
> **CantankRus said:**
> It's hard to know exactly what temperature the sensors output represents.
For me the purpose of sensors is to monitor my cpu temps and fans.
For the cpu temp I choose one that looks about right then run a cpu intensive application (eg youtube vid)
and if the temp fluctuates with cpu activity I'm happy to use it.
Have a look at the lm-sensors link in previous post.

```
Phoronix Test Suite v5.2.1
Interactive Benchmarking

System Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI 990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB, Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D, Graphics: MSI NVIDIA GeForce GTX 760 2048MB (1019/3004MHz), Audio: Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411



1: Run A Test
2: Run A Suite [A Collection Of Tests]
3: Run Complex System Test
4: Show System Hardware / Software Information
5: Show Auto-Detected System Sensors
6: Set Test Run Repetition
7: Backup Results To Media Storage
8: Exit
Select Task: 4

System Software / Hardware Information

Hardware:
Processor: AMD FX-9590 Eight-Core @ 4.70GHz (8 Cores), Motherboard: MSI 990FXA-GD65 (MS-7640) v3.0, Chipset: AMD RD890 bridge, Memory: 16384MB, Disk: 128GB Corsair Force GS + 2000GB Western Digital WD20EZRX-00D, Graphics: MSI NVIDIA GeForce GTX 760 2048MB (1019/3004MHz), Audio: Realtek ALC892, Monitor: LG E2250, Network: Realtek RTL8111/8168/8411

Software:
OS: Ubuntu 14.04, Kernel: 3.13.0-36-generic (x86_64), Desktop: Unity 7.2.2, Display Server: X Server 1.15.1, Display Driver: NVIDIA 331.38, OpenGL: 4.3.0, Compiler: GCC 4.8.2, File-System: ext4, Screen Resolution: 1920x1080




1: Run A Test
2: Run A Suite [A Collection Of Tests]
3: Run Complex System Test
4: Show System Hardware / Software Information
5: Show Auto-Detected System Sensors
6: Set Test Run Repetition
7: Backup Results To Media Storage
8: Exit
Select Task: 5

Detected System Sensors

CPU Fan Speed: 2392 RPM
CPU Frequency: 1400.00 Megahertz
CPU Power Consumption: 86.22 Watts
CPU Temperature: 4.63 Celsius
CPU Usage: 2.02 Percent
GPU Fan Speed: 34 Percent
GPU Frequency: 1019 Megahertz
GPU Temperature: 34 Celsius
GPU Usage: 1 Percent
Drive Read Speed: 0.00 MB/s
Drive Write Speed: 0.00 MB/s
Memory Usage: 2155 Megabytes
Network Usage: 0 Kilobytes/second
Swap Usage: 0 Megabytes
System Fan Speed: 1238 RPMs
System Iowait: 0.00 Percent
System Temperature: 29.00 Celsius
System V3 Voltage: 3.30 Volts

```

CPU Temperature: 4.63 Celsius << but if i use "sensors && inxi -s" cpu: 35.0C 

what real CPU temp?

```
koiv@koiv:~$ sensors && inxi -s
k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +7.2°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       81.88 W  (crit = 219.76 W)

f71889a-isa-0480
Adapter: ISA adapter
+3.3V:        +3.30 V  
in1:          +1.42 V  (max =  +2.04 V)
in2:          +1.50 V  
in3:          +0.95 V  
in4:          +1.08 V  
in5:          +1.09 V  
in6:          +1.14 V  
3VSB:         +3.31 V  
Vbat:         +3.28 V  
fan1:        2400 RPM
fan2:           0 RPM  ALARM
fan3:        1230 RPM
temp1:        +35.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +42.0°C  (high = +85.0°C, hyst = +79.0°C)
                       (crit = +107.0°C, hyst = +101.0°C)  sensor = thermistor
temp3:        +29.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

Sensors:   System Temperatures: cpu: 35.0C mobo: 42.0C gpu: 29C 
           Fan Speeds (in rpm): cpu: 2400 fan-2: 0 fan-3: 1230 
```

> sorry for my bad english, still work on it :D

---

### Post by CantankRus on 2014-09-29
I get similar results...
```
[COLOR="#006400"]**@Trusty:~$**[/COLOR] **sensors**
it8728-isa-0228
Adapter: ISA adapter
in0:          +0.84 V  (min =  +0.00 V, max =  +3.06 V)
in1:          +1.49 V  (min =  +0.00 V, max =  +3.06 V)
in2:          +1.99 V  (min =  +0.00 V, max =  +3.06 V)
+3.3V:        +3.22 V  (min =  +0.00 V, max =  +6.12 V)
in4:          +1.93 V  (min =  +0.00 V, max =  +3.06 V)
in5:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
in6:          +2.21 V  (min =  +0.00 V, max =  +3.06 V)
3VSB:         +3.26 V  (min =  +0.00 V, max =  +6.12 V)
Vbat:         +3.17 V  
fan1:        1967 RPM  (min =    0 RPM)
fan2:        1153 RPM  (min =    0 RPM)
fan3:           0 RPM  (min =    0 RPM)
temp1:        +29.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = thermistor
[COLOR="#FF0000"]temp2:        +28.0°C[/COLOR]  (low  = +127.0°C, high = +127.0°C)  sensor = thermal diode
temp3:        +22.0°C  (low  = +127.0°C, high = +127.0°C)  sensor = Intel PECI
intrusion0:  ALARM

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       53.96 W  (crit =  95.06 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:         +6.2°C  (high = +70.0°C)
                       (crit = +80.0°C, hyst = +77.0°C)

[COLOR="#006400"]**@Trusty:~$**[/COLOR] **inxi -s**
Sensors:   System Temperatures: [COLOR="#FF0000"]cpu: 28.0C[/COLOR] mobo: 15.4C gpu: 29C 
           Fan Speeds (in rpm): cpu: 1153 fan-1: 1956 fan-3: 0 

[COLOR="#006400"]**@Trusty:~$**[/COLOR] **phoronix-test-suite system-sensors**

Phoronix Test Suite v5.2.1
Supported Sensors

CPU Fan Speed: 2008 RPM
CPU Frequency: 1400.00 Megahertz
CPU Power Consumption: 64.40 Watts
[COLOR="#FF0000"]CPU Temperature: 6.00 Celsius[/COLOR]
CPU Usage: 1.77 Percent
GPU Fan Speed: 45 Percent
GPU Frequency: 969 Megahertz
GPU Temperature: 31 Celsius
Drive Read Speed: 0.00 MB/s
Drive Temperature: 32 Celsius
Drive Write Speed: 0.00 MB/s
Memory Usage: 2002 Megabytes
Network Usage: 0 Kilobytes/second
Swap Usage: 0 Megabytes
System Fan Speed: 1146 RPMs
System Iowait: 0.00 Percent
System Temperature: 26.00 Celsius
System V3 Voltage: 3.22 Volts

Unsupported Sensors

- CPU Voltage
- GPU Power Consumption
- GPU Usage
- GPU Voltage
- System Power Consumption
- System V12 Voltage
- System V5 Voltage
```

I can either go to [**_[COLOR="#B22222"]lm-sensors.org[/COLOR]_**]("http://www.lm-sensors.org/") and do a lot of reading and research on my hardware
or
select an output that behaves as I would expect.

---

