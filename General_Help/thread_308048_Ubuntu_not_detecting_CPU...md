---
title: "Ubuntu not detecting CPU.."
date: 2006-11-27
forum: General Help
---

### Post by deanhopkins on 2006-11-27
Hey. In ubuntu, I cant read temperatures of my CPU, etc.

I went to the device manager and found it came up as "Unknown Device". So, I went to the AMD site to download a linux frequency driver for my CPU, and it says this:

The powernow-k8.c and powernow-k8.h files should be 
placed in the arch/i386/kernel/cpu/cpufreq directory. 

I cant find the arch/ folder anywhere, is this different on Ubuntu or am I being silly?

Thanks.

Athlon 64 4600+ x2 AM2 (32bit Edgy EFT)

---

### Post by ssalman on 2006-11-27
what you have downloaded are a C language file (.c) and a C header file (.h) which should be included in the kernel when you compile it...

---

### Post by deanhopkins on 2006-11-27
Yeah, it tells me to put them in the arch/i386/kernel/cpu/cpufreq directory, then rebuild the kernel and reboot.

What exactly do I need to do, in terms a noob will understand :P

Thanks.

---

### Post by Kittie Rose on 2006-11-27
That has to be the funniest topic title ever :) 

I think "arch" could be shorthand for an archive file... maybe it accesses it inside a tar?

---

### Post by Ramses de Norre on 2006-11-27
No arch is short for architecture, the directory you're looking for is inside the source code of the linux kernel and if you want to use those things you'll need to compile your own kernel.. I haven't done this myself yet but there are good guides about it on the forums.

I wouldn't start with it if you don't feel comfortable in linux yet though, it certainly isn't too easy..

---

### Post by ssalman on 2006-11-27
[LEFT]here is a [link ]("https://wiki.ubuntu.com/KernelCustomBuild?highlight=%28kernel%29%7C%28compiling%29")to get you started, but I have to warn you... kernel compiling is not for newbies... you have to walk before you run, spend some time with linux before doing advanced stuff... just an advice.
[/LEFT]

---

### Post by deanhopkins on 2006-11-27
Cant really see myself doing that then. Im not a newbie really, Ive just never done stuff with the kernel like that, ive been using ubuntu for about 6 months now, i can fix my own problems nowadays (usually :P) and get around with no issues (usually :P)

Is there any other way I could get it to detect my CPU better? I overclock, and its always good to see my temps.

---

### Post by reclusivemonkey on 2006-11-28
> **deanhopkins said:**
> Cant really see myself doing that then. Im not a newbie really, Ive just never done stuff with the kernel like that, ive been using ubuntu for about 6 months now, i can fix my own problems nowadays (usually :P) and get around with no issues (usually :P)

Is there any other way I could get it to detect my CPU better? I overclock, and its always good to see my temps.

[LM Sensors]("http://ubuntuforums.org/showthread.php?t=2780&highlight=lm_sensors") is what you need.

---

### Post by deanhopkins on 2006-11-28
Lm_sensors doesnt read it either :(

---

### Post by reclusivemonkey on 2006-11-28
> **deanhopkins said:**
> Lm_sensors doesnt read it either :(

What does lm_sensors tell you?

---

### Post by deanhopkins on 2006-11-29
Heres a log of when I do sensors-detect:

```
dean@linux:~$ sudo sensors-detect
Password:
# sensors-detect revision 1.413 (2006/01/19 20:28:00)

This program will help you determine which I2C/SMBus modules you need to
load to use lm_sensors most effectively. You need to have i2c and
lm_sensors installed before running this program.
Also, you need to be `root', or at least have access to the /dev/i2c-*
files, for most things.
If you have patched your kernel and have some drivers built in, you can
safely answer NO if asked to load some modules. In this case, things may
seem a bit confusing, but they will still work.

It is generally safe and recommended to accept the default answers to all
questions, unless you know what you're doing.

 We can start with probing for (PCI) I2C or SMBus adapters.
 You do not need any special privileges for this.
 Do you want to probe now? (YES/no): yes
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no): yes
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: NVIDIA i2c adapter 2 at 0:05.0
Do you want to scan it? (YES/no/selectively): yes

Next adapter: NVIDIA i2c adapter 1 at 0:05.0
Do you want to scan it? (YES/no/selectively): yes     

Next adapter: NVIDIA i2c adapter 0 at 0:05.0
Do you want to scan it? (YES/no/selectively): yes
Client found at address 0x37
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Probing for `DDC monitor'... Success!
    (confidence 8, driver `eeprom'), other addresses: 0x51 0x52 0x53 0x54 0x55 0x56 0x57
Probing for `Maxim MAX6900'... Failed!
Client found at address 0x51
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x54
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Client found at address 0x55
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): yes
Probing for `National Semiconductor LM78'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM78-J'
  Trying address 0x0290... Failed!
Probing for `National Semiconductor LM79'
  Trying address 0x0290... Failed!
Probing for `Winbond W83781D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83782D'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627HF'
  Trying address 0x0290... Failed!
Probing for `Winbond W83627EHF'
  Trying address 0x0290... Failed!
Probing for `Silicon Integrated Systems SIS5595'
  Trying general detect... Failed!
Probing for `VIA Technologies VT82C686 Integrated Sensors'
  Trying general detect... Failed!
Probing for `VIA Technologies VT8231 Integrated Sensors'
  Trying general detect... Failed!
Probing for `ITE IT8712F'
  Trying address 0x0290... Success!
    (confidence 8, driver `it87')
Probing for `ITE IT8705F / SiS 950'
  Trying address 0x0290... Failed!
Probing for `IPMI BMC KCS'
  Trying address 0x0ca0... Failed!
Probing for `IPMI BMC SMIC'
  Trying address 0x0ca8... Failed!

Some Super I/O chips may also contain sensors. Super I/O probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x8716)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0x8716)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x8716)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): yes
Probing for `ITE 8702F Super IO Sensors'
  Failed! (skipping family)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

 Now follows a summary of the probes I have just done.
 Just press ENTER to continue: 

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 0:05.0'
    Busdriver `UNKNOWN', I2C address 0x50 (and 0x51 0x52 0x53 0x54 0x55 0x56 0x57)
    Chip `DDC monitor' (confidence: 8)

Driver `it87' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `ITE IT8712F' (confidence: 8)


I will now generate the commands needed to load the I2C modules.

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
# modprobe unknown adapter NVIDIA i2c adapter 0 at 0:05.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 0:05.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 0:05.0
i2c-isa
# I2C chip drivers
eeprom
it87
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)yes
dean@linux:~$ 

```

Then when I run sensors I get this:

```
dean@linux:~$ sensors
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
dean@linux:~$
```

---

### Post by reclusivemonkey on 2006-11-29
> **deanhopkins said:**
> 
For older kernels, make sure you have done 'modprobe i2c-proc'!
dean@linux:~$[/code]

Did you run the make devices script from the howto on this forum? Also what does lsmod say?

---

