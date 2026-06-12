---
title: "Enabling sensors"
date: 2007-01-24
forum: General Help
---

### Post by intrepidus on 2007-01-24
I've got a little Dell GX270 SFF I'm using Ubuntu Server on, and I want to monitor its temperature. Tried following: [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

But when I try sensors-detect I get:

```

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.

```

Since lm-sensors won't work, is there any other way to monitor?

---

### Post by matthewstory on 2007-01-24
you need to enable the i2c bus drivers and the lm-sensors modules:

sudo aptitude install modconf
sudo modconf

then surf around and plug in the lm-sensors modules and the i2c bus drivers.

---

### Post by intrepidus on 2007-01-24
> **matthewstory said:**
> you need to enable the i2c bus drivers and the lm-sensors modules:

sudo aptitude install modconf
sudo modconf

then surf around and plug in the lm-sensors modules and the i2c bus drivers.

I found the drivers in /kernel/drivers/i2c, and they were already enabled.

Not sure what you mean by "plug in the lm-sensors modules", but I have that installed.

Also, I forgot to include, but get this error when I run 'sensors':

```

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

```

---

### Post by trill on 2007-02-09
```
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!
```


I get this messsage too. Have you got the sensors working yet?

---

### Post by elcasey on 2007-03-19
Sorry to dredge up an old thread, but I've yet to find a single one where anyone addressed the issue in the above post.

What gives??? I have the same problem, and I'd like to know how to fix it!

---

### Post by scxtt on 2007-03-19
not sure that this'll help anyone ... but lm-sensors NEVER used to make sense to me until i thought of it this way:

install the package
probe for the driver my board requires

so at this point, i don't even need to do the "sensors-detect", since i know the name of the module i use ... i just make sure the module gets loaded @ boot ... i will say that w/in the output of sensors-detect, it should give you a very good idea of what module to use - it uses a rating/scale system, letting you know which one is the best choice ...

---

### Post by elcasey on 2007-03-20
But for many of us "sensors-detect" doesn't seem to work properly, as noted in trill's error message (which is the same one I get). The howtos don't help if they don't work with your particular hardware (I have a rather new system, with a Gigabyte GA-965P-S3 motherboard).

Here's the output of my "sensors-detect":

```
ch@centurion:~$ sensors-detect
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
 Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

As you are not root, we can't load adapter modules. We will only scan
already loaded adapters.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: NVIDIA i2c adapter 2 at 1:00.0
Do you want to scan it? (YES/no/selectively): 
Can't open /dev/i2c-2

Next adapter: NVIDIA i2c adapter 1 at 1:00.0
Do you want to scan it? (YES/no/selectively): 
ch@centurion:~$ sudo sensors-detect
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
 Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Sorry, no PCI bus adapters found.

We will now try to load each adapter module in turn.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

Next adapter: NVIDIA i2c adapter 2 at 1:00.0
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter 1 at 1:00.0
Do you want to scan it? (YES/no/selectively): 

Next adapter: NVIDIA i2c adapter 0 at 1:00.0
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x35
Client found at address 0x3e
Client found at address 0x4a
Probing for `National Semiconductor LM75'... Failed!
Probing for `National Semiconductor LM77'... Failed!
Probing for `Dallas Semiconductor DS1621'... Failed!
Probing for `National Semiconductor LM92'... Failed!
Probing for `National Semiconductor LM76'... Success!
    (confidence 2, driver `lm92')
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Success!
    (confidence 2, driver `lm92')
Client found at address 0x4b
Probing for `National Semiconductor LM75'... Failed!
Probing for `National Semiconductor LM77'... Failed!
Probing for `Dallas Semiconductor DS1621'... Failed!
Probing for `Maxim MAX6650/MAX6651'... Success!
    (confidence 4, driver `max6650')
Probing for `National Semiconductor LM92'... Failed!
Probing for `National Semiconductor LM76'... Success!
    (confidence 2, driver `lm92')
Probing for `Maxim MAX6633/MAX6634/MAX6635'... Success!
    (confidence 2, driver `lm92')
Client found at address 0x50
Probing for `SPD EEPROM'... Success!
    (confidence 1, driver `eeprom')
Probing for `DDC monitor'... Success!
    (confidence 8, driver `eeprom'), other addresses: 0x51 0x52 0x53 0x54 0x55 0x56 0x57
Probing for `Maxim MAX6900'... Failed!

Some chips are also accessible through the ISA bus. ISA probes are
typically a bit more dangerous, as we have to write to I/O ports to do
this. This is usually safe though.

Do you want to scan the ISA bus? (YES/no): 
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

Do you want to scan for Super I/O sensors? (YES/no): 
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0x8718)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0x8718)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x8718)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (skipping family)
Probing for `VT1211 Super IO Sensors'
  Failed! (skipping family)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (skipping family)

Do you want to scan for secondary Super I/O sensors? (YES/no): 
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

Driver `lm92' (should be inserted but causes problems):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x4a
    Chip `National Semiconductor LM76' (confidence: 2)
  Misdetects:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `National Semiconductor LM76' (confidence: 2)
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6633/MAX6634/MAX6635' (confidence: 2)

Driver `max6650' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
    Busdriver `UNKNOWN', I2C address 0x4b
    Chip `Maxim MAX6650/MAX6651' (confidence: 4)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `NVIDIA i2c adapter 0 at 1:00.0'
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
# modprobe unknown adapter NVIDIA i2c adapter 0 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 1 at 1:00.0
# modprobe unknown adapter NVIDIA i2c adapter 2 at 1:00.0
i2c-isa
# I2C chip drivers
lm92
# Warning: the required module max6650 is not currently installed on your system.
# For status of 2.6 kernel ports see http://secure.netroedge.com/~lm78/supported.html
# If driver is built-in to the kernel, or unavailable, comment out the following line.
max6650
eeprom
it87
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)
```

---

### Post by scxtt on 2007-03-20
can you post everything that sensors-detect outputs?

and it's quite possible that lm-sensors just doesn't support your chip :(

my motherboard is a few years old, 3 tops ... and all i need to do to get sensors going is **sudo aptitude install lm-sensors** then load the module - then i can run sensors -f and see its output ... so i don't have to worry about i2c or dependencies from it - i don't use sensors-detect @ all since i know the module name ...

maybe you can find out what module it uses independent of lm-sensors and then do a modprobe on it ... i think there's a windows program (CPU-Z) that will tell you what it is - if your BIOS doesn't and the user manual doesn't - it can't be a secret ...

---

### Post by elcasey on 2007-03-20
My sensors-detect output is above. Apparently it does work correctly after all, but the "max6650" driver is apparently "missing," and the other drivers are all inserted. modprobe.d/local is entirely useless since it describes every line as a "bad line" to be ignored if I run, for example, "modprobe lm92." 

I commented out every line modprobe.d/local and when I modprobe the drivers, I get no output (because they're already loaded) except for "max6650," because it's not there. How do I install this driver? Where can I find it?

I thought the days of Linux having rather serious hardware issues were over, but between this and the JMicron IDE controller issue (which will supposedly be fixed in Herd 6), I'm beginning to believe that that's anything but the case.

It's certainly not catastrophic if I can't get sensor readings, but it's very disappointing. It's not like I'm using a PC Chips motherboard! :rolleyes:

---

### Post by elcasey on 2007-03-20
I found this - [http://lm-sensors.org/changeset/4344](http://lm-sensors.org/changeset/4344) - but I have no clue what it means! :mrgreen: 

Thanks for the help, scxtt, I'm really hoping to get this resolved since it seems that the missing max6650 driver is the only obstacle here.
When I run the Hardware Sensors applet in the panel, I get a "No Sensors Found!" message but perhaps that's dependent on the max driver. But why wouldn't it communicate with the i2c, im92, eeprom, etc. drivers??

I searched for and installed "libsensors3" and "libsensors-dev," but how can I know if these packages were compiled with sysfs support? Isn't this something that should've been handled by lm-sensors?

EDIT: Figured out how to mount sysfs and added it to fstab.

---

### Post by scxtt on 2007-03-20
well, i have a lm92 sensor available - so you should too ... are you doing **sudo modprobe lm92** or just **modprobe lm92**?

you might also want to see what this is:
```
[font=courier]:> slocate max6650
/usr/share/doc/lm-sensors/doc/chips/max6650.gz[/font]
```

---

### Post by Linuturk on 2007-03-31
I have a similar problem.

Here are some outputs:
```

$ lsmod | grep i2c
i2c_dev                10500  0 
i2c_ec                  6272  1 sbs
i2c_core               23424  2 i2c_dev,i2c_ec
```

the mkdev.sh script created the devices under /dev/

```
$ sudo sensors-detect 
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
i2c-dev is already loaded.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

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
  Trying address 0x0290... Failed!
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
  Failed! (0x3c00)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0x3c00)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0x3c00)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87591 Super IO'
  Failed! (0x3c)
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0x3c)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0x3c)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0x3c)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0x3c)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0x3c)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47M15x/192/997 Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0x3c)
Probing for `SMSC 47M172 Super IO'
  Failed! (0x3c)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0x3c)
Probing for `SMSC SCH5307-NS Super IO'
  Failed! (0x3c)
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

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 [http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html](http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html)
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 [http://secure.netroedge.com/~lm78/newdrivers.html](http://secure.netroedge.com/~lm78/newdrivers.html) for driver status.
```

Any ideas folks?

---

### Post by scxtt on 2007-04-01
can you get i2c-isa loaded?

---

### Post by Linuturk on 2007-04-01
how would I load that?

---

### Post by scxtt on 2007-04-01
**modprobe -l | grep i2c-isa** (to make sure you have it)
**sudo modprobe i2c-isa** (to get it loaded)

---

### Post by Linuturk on 2007-04-01
ok, I loaded the module, but the sensors-detect still doesn't detect any sensors.

---

### Post by confused57 on 2007-04-01
> **Linuturk said:**
> ok, I loaded the module, but the sensors-detect still doesn't detect any sensors.
My Dell Dimension doesn't have any temperature detecting chipsets, I've tried Motherboard Monitor in Windows & lm-sensors in Ubuntu...neither would work.
Go into your bios setup, unless you have an option for detecting hardware temperatures, you're probably out of luck.
On my 2 other pc's, I can go into bios and get temperature, fan, voltage, etc readings and lm-sensors work quite well on both of them.

---

### Post by Linuturk on 2007-04-01
I was able to monitor temps and everything with Mobile Meter on Windows, so the sensors must be there.

---

### Post by loko on 2007-04-08
hello,

I followed the complete thread, tried everthing mentioned in here, but it doesn't help, i always get:

```
user@laptop:~$ sensors -f
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.
user@laptop:~$
```

Can somebody help, who have it working with the same output?

here is the output of sensors-detect on my system:

```
user@laptop:~$ sudo sensors-detect
# sensors-detect revision 4171 (2006-09-24 03:37:01 -0700)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

We can start with probing for (PCI) I2C or SMBus adapters.
Do you want to probe now? (YES/no): 
Probing for PCI bus adapters...
Use driver `i2c-i801' for device 0000:00:1f.3: Intel ICH7

We will now try to load each adapter module in turn.
Module `i2c-i801' already loaded.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

We are now going to do the I2C/SMBus adapter probings. Some chips may
be double detected; we choose the one with the highest confidence
value in that case.
If you found that the adapter hung after probing a certain address,
you can specify that address to remain unprobed.

Next adapter: SMBus I801 adapter at 0400
Do you want to scan it? (YES/no/selectively): 
Client found at address 0x2e
Probing for `Myson MTP008'...                               No
Probing for `National Semiconductor LM78'...                No
Probing for `National Semiconductor LM78-J'...              No
Probing for `National Semiconductor LM79'...                No
Probing for `National Semiconductor LM80'...                No
Probing for `National Semiconductor LM85 or LM96000'...     No
Probing for `Analog Devices ADM1027, ADT7460 or ADT7463'... No
Probing for `SMSC EMC6D100, EMC6D101 or EMC6D102'...        No
Probing for `Analog Devices ADT7462'...                     No
Probing for `Analog Devices ADT7467 or ADT7468'...          No
Probing for `Analog Devices ADT7470'...                     No
Probing for `Analog Devices ADT7473'...                     Success!
    (confidence 5, driver `to-be-written')
Probing for `Analog Devices ADT7475'...                     No
Probing for `Analog Devices ADT7476'...                     No
Probing for `National Semiconductor LM87'...                No
Probing for `National Semiconductor LM93'...                No
Probing for `Winbond W83781D'...                            No
Probing for `Winbond W83782D'...                            No
Probing for `Winbond W83792D'...                            No
Probing for `Winbond W83793R/G'...                          No
Probing for `Winbond W83791SD'...                           No
Probing for `Winbond W83627HF'...                           No
Probing for `Winbond W83627EHF'...                          No
Probing for `Winbond W83627DHG'...                          No
Probing for `Asus AS99127F (rev.1)'...                      No
Probing for `Asus AS99127F (rev.2)'...                      No
Probing for `Asus ASB100 Bach'...                           No
Probing for `Winbond W83L785TS-S'...                        No
Probing for `Analog Devices ADM9240'...                     No
Probing for `Dallas Semiconductor DS1780'...                No
Probing for `National Semiconductor LM81'...                No
Probing for `Analog Devices ADM1026'...                     No
Probing for `Analog Devices ADM1025'...                     No
Probing for `Analog Devices ADM1024'...                     No
Probing for `Analog Devices ADM1029'...                     No
Probing for `Analog Devices ADM1030'...                     No
Probing for `Analog Devices ADM1031'...                     No
Probing for `Analog Devices ADM1022'...                     No
Probing for `Texas Instruments THMC50'...                   No
Probing for `Analog Devices ADM1028'...                     No
Probing for `ITE IT8712F'...                                No
Probing for `Fintek F75373S/SG'...                          No
Probing for `Fintek F75375S/SP'...                          No
Probing for `Fintek F75387SG/RG'...                         No
Probing for `Winbond W83791D'...                            No
Client found at address 0x50
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x51
Handled by driver `eeprom' (already loaded), chip type `eeprom'
Client found at address 0x69

Some chips are also accessible through the ISA I/O ports. We have to
write to arbitrary I/O ports to probe them. This is usually safe though.
Yes, you do have ISA I/O ports even if you do not have any ISA slots!
Do you want to scan the ISA I/O ports? (YES/no): 
Probing for `National Semiconductor LM78' at 0x290...       No
Probing for `National Semiconductor LM78-J' at 0x290...     No
Probing for `National Semiconductor LM79' at 0x290...       No
Probing for `Winbond W83781D' at 0x290...                   No
Probing for `Winbond W83782D' at 0x290...                   No
Probing for `Winbond W83627HF' at 0x290...                  No
Probing for `Silicon Integrated Systems SIS5595'...         No
Probing for `VIA VT82C686 Integrated Sensors'...            No
Probing for `VIA VT8231 Integrated Sensors'...              No
Probing for `AMD K8 thermal sensors'...                     No
Probing for `IPMI BMC KCS' at 0xca0...                      No
Probing for `IPMI BMC SMIC' at 0xca8...                     No

Some Super I/O chips may also contain sensors. We have to write to
standard I/O ports to probe them. This is usually safe.
Do you want to scan for Super I/O sensors? (YES/no): 
Probing for Super-I/O at 0x2e/0x2f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No
Probing for Super-I/O at 0x4e/0x4f
Trying family `ITE'...                                      No
Trying family `National Semiconductor'...                   No
Trying family `SMSC'...                                     No
Trying family `VIA/Winbond/Fintek'...                       No

Now follows a summary of the probes I have just done.
Just press ENTER to continue: 

Driver `to-be-written' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x2e
    Chip `Analog Devices ADT7473' (confidence: 5)

Driver `eeprom' (should be inserted):
  Detects correctly:
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x50
    Chip `eeprom' (confidence: 6)
  * Bus `SMBus I801 adapter at 0400'
    Busdriver `i2c-i801', I2C address 0x51
    Chip `eeprom' (confidence: 6)

  EEPROMs are *NOT* sensors! They are data storage chips commonly
  found on memory modules (SPD), in monitors (EDID), or in some
  laptops, for example.

I will now generate the commands needed to load the required modules.
Just press ENTER to continue: 

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-i801
# Chip drivers
# no driver for Analog Devices ADT7473 yet
eeprom
#----cut here----


Do you want to add these lines to /etc/modules automatically? (yes/NO)
user@laptop:~$ 
```

---

### Post by loko on 2007-04-08
ok,

i found out what the problem is.

i have Intel Core DUO.

lmsensors need the coretemp-module in the kernel, which is not in the ubuntu-kernel.

if somebody need it, here is the patch:

[http://www.debianhelp.org/node/5156](http://www.debianhelp.org/node/5156)

---

