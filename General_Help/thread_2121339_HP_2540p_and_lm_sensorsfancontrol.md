---
title: "HP 2540p and lm_sensors/fancontrol"
date: 2013-03-01
forum: General Help
---

### Post by vickoxy on 2013-03-01
Hi,
i have one HP 2540p with i7 Processor and try to make fancontrol working because the fan i always on.

sensors-detect gives me:

```
root@linux:~# sensors-detect
# sensors-detect revision 5984 (2011-07-10 21:22:53 +0200)
# System: Hewlett-Packard HP EliteBook 2540p (laptop)
# Board: Hewlett-Packard 7008

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
Trying family `SMSC'...                                     Yes
Found `SMSC FDC37B72x Super IO'                             
    (no hardware monitoring capabilities)
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
Sorry, no supported PCI bus adapters found.
Module i2c-dev loaded successfully.

Next adapter: i915 gmbus disabled (i2c-0)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus ssc (i2c-1)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOB (i2c-2)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus vga (i2c-3)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOA (i2c-4)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus panel (i2c-5)
Do you want to scan it? (YES/no/selectively): y
 
Next adapter: i915 GPIOC (i2c-6)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpc (i2c-7)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOD (i2c-8)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus dpb (i2c-9)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOE (i2c-10)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 gmbus reserved (i2c-11)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x18
Probing for `Analog Devices ADM1021'...                     No
Probing for `Analog Devices ADM1021A/ADM1023'...            No
Probing for `Maxim MAX1617'...                              No
Probing for `Maxim MAX1617A'...                             No
Probing for `Maxim MAX1668'...                              No
Probing for `Maxim MAX1805'...                              No
Probing for `Maxim MAX1989'...                              No
Probing for `Maxim MAX6655/MAX6656'...                      No
Probing for `TI THMC10'...                                  No
Probing for `National Semiconductor LM84'...                No
Probing for `Genesys Logic GL523SM'...                      No
Probing for `Onsemi MC1066'...                              No
Probing for `Maxim MAX1618'...                              No
Probing for `Maxim MAX1619'...                              No
Probing for `National Semiconductor LM82/LM83'...           No
Probing for `Maxim MAX6654'...                              No
Probing for `Maxim MAX6690'...                              No
Probing for `Maxim MAX6680/MAX6681'...                      No
Probing for `Maxim MAX6695/MAX6696'...                      No
Probing for `Texas Instruments AMC6821'...                  No
Probing for `National Semiconductor LM95245'...             No
Probing for `National Semiconductor LM64'...                No
Probing for `SMSC EMC1047'...                               No
Probing for `SMSC EMC1402'...                               No
Probing for `SMSC EMC1403'...                               No
Probing for `SMSC EMC1404'...                               No
Probing for `ST STTS424'...                                 No
Probing for `ST STTS424E'...                                No
Probing for `NXP SE97/SE97B'...                             No
Probing for `NXP SE98'...                                   No
Probing for `Analog Devices ADT7408'...                     No
Probing for `IDT TS3000/TSE2002'...                         No
Probing for `Maxim MAX6604'...                              No
Probing for `Microchip MCP98242'...                         No
Probing for `Microchip MCP98243'...                         No
Probing for `Microchip MCP9843'...                          No
Probing for `ON CAT6095/CAT34TS02'...                       No
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                No
Client found at address 0x51
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x52
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x53
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Client found at address 0x58
Probing for `Analog Devices ADT7462'...                     No
Probing for `Andigilog aSC7512'...                          No
Client found at address 0x5c
Probing for `Analog Devices ADT7462'...                     No
Probing for `SMSC EMC1072'...                               No
Probing for `SMSC EMC1073'...                               No
Probing for `SMSC EMC1074'...                               No
Client found at address 0x73
Probing for `FSC Poseidon I'...                             No
Probing for `FSC Poseidon II'...                            No
Probing for `FSC Scylla'...                                 No
Probing for `FSC Hermes'...                                 No
Probing for `FSC Heimdal'...                                No
Probing for `FSC Heracles'...                               No
Probing for `FSC Hades'...                                  No
Probing for `FSC Syleus'...                                 No

Next adapter: i915 gmbus dpd (i2c-12)
Do you want to scan it? (YES/no/selectively): y

Next adapter: i915 GPIOF (i2c-13)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-A (i2c-14)
Do you want to scan it? (YES/no/selectively): y
Client found at address 0x50
Probing for `Analog Devices ADM1033'...                     No
Probing for `Analog Devices ADM1034'...                     No
Probing for `SPD EEPROM'...                                 No
Probing for `EDID EEPROM'...                                Yes
    (confidence 8, not a hardware monitoring chip)

Next adapter: DPDDC-B (i2c-15)
Do you want to scan it? (YES/no/selectively): y

Next adapter: DPDDC-D (i2c-16)
Do you want to scan it? (YES/no/selectively): y

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
loaded. You may want to run 'service module-init-tools start'
to load them.

Unloading i2c-dev... OK
Unloading cpuid... OK
```

sudo pwmconfig:
```
root@linux:~# sudo pwmconfig
# pwmconfig revision 5857 (2010-08-22)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```

So, i know that is crucially to make lm-sensors working to make fancontrol working. But i found no help... So i am thankful for any help

---

### Post by Toz on 2013-03-01
> the fan i always on
Which video card does it have? 

Have you tried any kernel boot parameters? I'd suggest **acpi_osi=** and **acpi_osi=Linux**. See the link in my signature on how to temporarily test kernel boot parameters.

---

### Post by vickoxy on 2013-03-01
Yes i tried some:
> GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt" 

The Card is: Intel Graphics Media Accelerator HD Graphics, GMA HD, or Intel HD Graphics (or GMA5700MHD) 
Thanks!

---

### Post by Toz on 2013-03-01
What is your current kernel boot command line:
```
cat /proc/cmdline
```

I'm not exactly sure what happens when you use multiple **GRUB_CMDLINE_LINUX=""**  and **GRUB_CMDLINE_LINUX_DEFAULT** lines. I have a feeling only the last one is used.

---

### Post by vickoxy on 2013-03-02
linux@linux:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=89e0895f-cb4e-4ac9-bced-912f1be5366d ro acpi_enforce_resources=lax quiet splash acpi=copy_dsdt vt.handoff=

---

### Post by vickoxy on 2013-03-02
I just reinstalled the system. Not sure what should i load to have lm-sensors? acpi or i8k (but, does´nt it works only with dell?)
So, after i  load the parameter i should run sensors-detect or pwmconfig?
Thanks and regards.

I noticed that temp 3 is actually FAN speed-as soon as it goes of, it stays 0, and for every further step the temp goes 10 grades up. But no idea what schould i do with this info.

```
acpitz-virtual-0
Adapter: Virtual device
temp1:         +0.0°C  (crit = +127.0°C)
temp2:         +0.0°C  (crit = +127.0°C)
temp3:        +11.0°C  (crit = +128.0°C)
temp4:        +39.0°C  (crit = +127.0°C)
temp5:         +0.0°C  (crit = +115.0°C)
temp6:        +32.2°C  (crit = +128.0°C)
temp7:         +0.0°C  (crit = +128.0°C)
temp8:        +42.0°C  (crit = +128.0°C)
temp9:        +48.0°C  (crit = +128.0°C)
temp10:       +59.0°C  (crit = +128.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +43.0°C  (high = +95.0°C, crit = +105.0°C)
Core 2:       +41.0°C  (high = +95.0°C, crit = +105.0°C)

```

---

### Post by vickoxy on 2013-03-03
I found here some help-can control fan but just for a short time. So if someone can help me i would be thankful.
[http://ubuntuforums.org/showthread.php?t=2008756&page=2](http://ubuntuforums.org/showthread.php?t=2008756&page=2)

---

### Post by vickoxy on 2013-03-03
No one?

---

### Post by Toz on 2013-03-03
> **vickoxy said:**
> Yes i tried some:
> 
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_CMDLINE_LINUX="acpi_enforce_resources=lax"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=\\\"Linux\\\""
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=copy_dsdt" 

The Card is: Intel Graphics Media Accelerator HD Graphics, GMA HD, or Intel HD Graphics (or GMA5700MHD) 
Thanks!

> **vickoxy said:**
> linux@linux:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=89e0895f-cb4e-4ac9-bced-912f1be5366d ro acpi_enforce_resources=lax quiet splash acpi=copy_dsdt vt.handoff=

Sorry for the delay in responding.
It looks like only the last instances of GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT are being used. I know you have re-installed your system and are looking at fan control mechanisms, but you might want to try a couple of kernel boot parameters to see if they help with the fan control. The first would be **acpi_osi=** and the second one would be **acpi_osi=Linux**. Make sure you try them separately and that you only have one GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT line in your /etc/default/grub command. Also make sure to run "sudo update-grub" after the change.

To confirm that the boot parameters are beign used, report back the results of:
```
cat /proc/cmdline
``` 
...after each attempt. See if either of these help with fan control.

---

### Post by vickoxy on 2013-03-03
```
linux@linux:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=725ffdaa-2101-4bd9-bc6e-bf5e87b3eb8d ro quiet splash vt.handoff=7 acpi_osi=

``` with this otpion i can not adjust screen brightness
```
sudo pwmconfig
``` gives me ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed

```
After ```
Sudo sensors-detect
``` no changes too


acpi_osi=Linux:

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-38-generic root=UUID=725ffdaa-2101-4bd9-bc6e-bf5e87b3eb8d ro quiet splash vt.handoff=7 acpi_osi=Linux

```

I can adjust brightness fine. ```
sudo pwmconfig
``` gives again: ```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
```
linux@linux:~$ service module-init-tools start
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.50" (uid=1000 pid=2940 comm="start module-init-tools ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

``` after ```
sensors-detect
```

---

### Post by vickoxy on 2013-03-03
Here is the fancontrol:
```
linux@linux:~$ sudo fancontrol
Loading configuration from /etc/fancontrol ...

Common settings:
  INTERVAL=10

Settings for hwmon0/device/pwm1:
  Depends on hwmon0/temp8_input
  Controls hwmon0/temp3_input
  MINTEMP=51
  MAXTEMP=53
  MINSTART=2
  MINSTOP=0
  MINPWM=0
  MAXPWM=255

Configuration is too old, please run pwmconfig again
linux@linux:~$ sensors
```

Where temp8_input is the nearest sensor to cpu temp (temp1 and temp2 are always 0). And temp3_input is the fan speed showing 11 or 21 or 31 C-why, i have no idea.
Maybe if i can insert some new fancontrol.conf without pwmconfig, but have no idea which one.
Here is my:
```
INTERVAL=10
FCTEMPS= hwmon0/device/pwm1=hwmon0/temp8_input
FCFANS= hwmon0/device/pwm1=hwmon0/temp3_input
MINTEMP= hwmon0/device/pwm1=51
MAXTEMP= hwmon0/device/pwm1=53
MINSTART= hwmon0/device/pwm1=2
MINSTOP= hwmon0/device/pwm1=0
MINPWM= hwmon0/device/pwm1=0
MAXPWM= hwmon0/device/pwm1=255
```

---

### Post by ogrozion on 2013-04-07
Howdy folks, I've bought a 2540p, its running 12.1, and my fan is stucked... Differently than yours, it stops during kernel bootup. The BIOS was updated to the last issue (03/2013). Did you had success with fancontrol? Or only with the fanslow.sh?
Thanks in advance, 
    Andrei Mörsch Franco

---

### Post by vickoxy on 2013-04-08
Well, i sold my HP 2540 and did not test any fancontrol-it was just too loud for me. So, unfortunately-i ain´t of any help here.

---

