---
title: "LXPanel: how to set up the Temperature Monitor?"
date: 2013-05-24
forum: General Help
---

### Post by xichael on 2013-05-24
I've installed lm-sensors, and the sensors command gives me a proper read of the temperature:
```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +66.0°C  (crit = +100.0°C)
```

But in LXPanel's Temperature Monitor applet, it only shows: **-273**

Do I need to put something specific in the sensor location box?

I did run sensors-detect, but not sure what I'm supposed to do with this information:

```

# sensors-detect revision 6031 (2012-03-07 17:14:01 +0100)
# System: Dell Inc. Inspiron 1018 [A00] (laptop)
# Board: Dell Inc. 0GHG2G


This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.


Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
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
Intel digital thermal sensor...                             Success!
    (driver `coretemp')
Intel AMB FB-DIMM thermal sensor...                         No
VIA C7 thermal sensor...                                    No
VIA Nano thermal sensor...                                  No


Some Super I/O chips contain embedded sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): y
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor/ITE'...               No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Nuvoton/Fintek'...               No
Trying family `ITE'...                                      No


Some hardware monitoring chips are accessible through the ISA I/O ports.
We have to write to arbitrary I/O ports to probe them. This is usually
safe though. Yes, you do have ISA I/O ports even if you do not have any
ISA slots! Do you want to scan the ISA I/O ports? (YES/no): y
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No


Lastly, we can probe the I2C/SMBus adapters for connected hardware
monitoring devices. This is the most risky part, and while it works
reasonably well on most systems, it has been reported to cause trouble
on some systems.
Do you want to probe the I2C/SMBus adapters now? (YES/no): y
Using driver `i2c-i801' for device 0000:00:1f.3: Intel 82801G ICH7
Module i2c-i801 loaded successfully.
Module i2c-dev loaded successfully.


Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (YES/no/selectively): y


Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (YES/no/selectively): y


Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x28
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM96080'...             No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG/W83667HG/W83677HG'...        No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Analog Devices ADM1029'...                     No
Probing for `ITE IT8712F'...                                No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)


Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (YES/no/selectively): y


Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (YES/no/selectively): y


Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (YES/no/selectively): y


Next adapter: SMBus I801 adapter at 18a0 (i2c-6)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 Yes
    (confidence 8, not a hardware monitoring chip)
Probing for `EDID EEPROM'...                                No


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


Do you want to add these lines automatically to /etc/modules? (yes/NO)y
Successful!


Monitoring programs won't work until the needed modules are
loaded. You may want to run 'service kmod start'
to load them.


Unloading i2c-dev... OK
Unloading i2c-i801... OK
Unloading cpuid... OK

```

---

### Post by Dennis N on 2013-05-24
It's broken, and has been for years:

[COLOR="#FF0000"]**[Edit: Not broken at least in Lubuntu 13.04 see post #3, 4, and 5]**[/COLOR]

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661224](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=661224)
[https://bbs.archlinux.org/viewtopic.php?id=160487](https://bbs.archlinux.org/viewtopic.php?id=160487)
[http://forum.lxde.org/viewtopic.php?t=1263&f=21](http://forum.lxde.org/viewtopic.php?t=1263&f=21)
[http://www.pclinuxos.com/forum/index.php?topic=93646.0](http://www.pclinuxos.com/forum/index.php?topic=93646.0)
[http://askubuntu.com/questions/229929/correct-sensor-location-to-use-for-temperature-monitor-in-lxpanel](http://askubuntu.com/questions/229929/correct-sensor-location-to-use-for-temperature-monitor-in-lxpanel)

---

### Post by vasa1 on 2013-05-24
I did not install [FONT=Courier New]lm-sensors[/FONT] and checked that it isn't installed using [FONT=Courier New]dpkg --get-selections[/FONT]. But the Temperature Monitor works for me in 13.04 and worked in 12.10 as well. I'm not sure if it works in all respects but there's a good correlation between the temp displayed and CPU activity. (I have those two side by side ). This is how mine is set up:

---

### Post by Dennis N on 2013-05-24
> **vasa1 said:**
> I did not install [FONT=Courier New]lm-sensors[/FONT] and checked that it isn't installed using [FONT=Courier New]dpkg --get-selections[/FONT]. But the Temperature Monitor works for me in 13.04 and worked in 12.10 as well. I'm not sure if it works in all respects but there's a good correlation between the temp displayed and CPU activity. (I have those two side by side ). This is how mine is set up:

Good news! No lm-sensors needed as well. I will try it in a few minutes - need to start up my laptop for Lubuntu 13.04.

---

### Post by Dennis N on 2013-05-24
**@vasa1**

OK, it is working. Changed the text color and positioned it and that's all. Thanks for the heads-up on this.

also, P.M. sent to xichael

Edit - Tried in Lubuntu 12.10 and still broken in that release for me. It shows the number -273. No lm-sensors installed. So I only have it working in Lubuntu 13.04.

---

### Post by xichael on 2013-05-25
-273 is all I get as well...

---

### Post by Catalanoic on 2013-05-28
For me works OK LXPanel and in Terminal (writting: *sensors*).

---

### Post by vasa1 on 2013-06-22
> **Dennis N said:**
> **@vasa1**

OK, it is working. Changed the text color and positioned it and that's all. Thanks for the heads-up on this.
...
Edit - Tried in Lubuntu 12.10 and still broken in that release for me. It shows the number -273. No lm-sensors installed. So I only have it working in Lubuntu 13.04.

@Dennis N; I've joined the -273 club :(
I set up VirtualBox with Lubuntu 13.04 both as host and guest (because I'm totally new to VBox and would like something I'm familiar with.) Long story short is in the image below. I tried repositioning it and changing the font color but no luck. Both systems are fully updated and, as before, I haven't installed lmsensors.

---

### Post by Dennis N on 2013-06-22
> **vasa1 said:**
> @Dennis N; I've joined the -273 club :(
I set up VirtualBox with Lubuntu 13.04... 

I haven't used VirtualBox since having it on Ubuntu 8.04, so I have no V.B. to test on anymore. I gather your problem is that the panel temp. indicator isn't working in Lubuntu in VirtualBox? For that, I don't have any ideas. Sorry.

Installs in virtual machines didn't perform quite the same in some ways as real installations. That's one take-away from using them. 

I would be curious if lm-sensors works in the V.B. Lubuntu and gives readings in the terminal?

---

### Post by vasa1 on 2013-06-22
> **Dennis N said:**
> ...
Installs in virtual machines didn't perform quite the same in some ways as real installations. That's one take-away from using them. 

I would be curious if lm-sensors works in the V.B. Lubuntu and gives readings in the terminal?

Yes, I'm finding that out as well!

I installed lm-sensors and then ran "sudo sensors-detect" and this is what I got (after answering "yes" to everything):
```
Sorry, no sensors were detected.
Either your system has no sensors, or they are not supported, or
they are connected to an I2C or SMBus adapter that is not
supported. If you find out what chips are on your board, check
http://www.lm-sensors.org/wiki/Devices for driver status.
vasa1@vasa1-VirtualBox:~$ 
```

Then I did the same thing on the host and after a few adventures, I got:

```

[11:45 AM] ~ $ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +49.5°C  (crit = +93.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +90.0°C, crit = +90.0°C)
Core 1:       +47.0°C  (high = +90.0°C, crit = +90.0°C)

```

And the temp1 +49.5°C is close to what the monitor in lxpanel had at the time. So one more example of VMs differing from real life :(

---

### Post by vasa1 on 2013-06-24
FWIW, when I hover the mouse over the temp indicator in lxpanel, I see this for the host OS (Lubuntu 13.04):

---

