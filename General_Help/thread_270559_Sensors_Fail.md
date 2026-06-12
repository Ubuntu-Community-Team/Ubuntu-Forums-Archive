---
title: "Sensors Fail"
date: 2006-10-03
forum: General Help
---

### Post by calvinthomas on 2006-10-03
Hi, I have looked at other threads on this but they're all really old and haven't solved my problem so I thought i'd start a new thread:

So I installed lm-sensors and ran sensors-detect and got this message:

```
No i2c device files found. Use prog/mkdev/mkdev.sh to create them.
```

So I followed the advice on another thread and made the script that says this:

```
#!/bin/bash

# Here you can set several defaults.

# The number of devices to create (max: 256)
NUMBER=32

# The owner and group of the devices
OUSER=root
OGROUP=root
# The mode of the devices
MODE=600

# This script doesn't need to be run if devfs is used
if [ -r /proc/mounts ] ; then
if grep -q "/dev devfs" /proc/mounts ; then
echo "You do not need to run this script as your system uses devfs."
exit;
fi
fi

i=0;

while [ $i -lt $NUMBER ] ; do
echo /dev/i2c-$i
mknod -m $MODE /dev/i2c-$i c 89 $i || exit
chown "$OUSER:$OGROUP" /dev/i2c-$i || exit
i=$[$i + 1]
done
#end of file
```

I ran this script and got this:

```
/dev/i2c-0
/dev/i2c-1
/dev/i2c-2
/dev/i2c-3
/dev/i2c-4
/dev/i2c-5
/dev/i2c-6
/dev/i2c-7
/dev/i2c-8
/dev/i2c-9
/dev/i2c-10
/dev/i2c-11
/dev/i2c-12
/dev/i2c-13
/dev/i2c-14
/dev/i2c-15
/dev/i2c-16
/dev/i2c-17
/dev/i2c-18
/dev/i2c-19
/dev/i2c-20
/dev/i2c-21
/dev/i2c-22
/dev/i2c-23
/dev/i2c-24
/dev/i2c-25
/dev/i2c-26
/dev/i2c-27
/dev/i2c-28
/dev/i2c-29
/dev/i2c-30
/dev/i2c-31
```


I then ran sensors-detect and now said YES to all of the questions and this is my output (running as root):

```
# sensors-detect revision 1.393 (2005/08/30 18:51:18)

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
Use driver `to-be-written' for device 00:14.0: ATI Technologies Inc ATI SMBus
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Load `to-be-written' (say NO if built into your kernel)? (YES/no):
FATAL: Module to_be_written not found.
Loading failed... skipping.
If you have undetectable or unsupported adapters, you can have them
scanned by manually loading the modules before running this script.

 To continue, we need module `i2c-dev' to be loaded.
 If it is built-in into your kernel, you can safely skip this.
 i2c-dev is not loaded. Do you want to load it now? (YES/no):
 Module loaded succesfully.

 We are now going to do the adapter probings. Some adapters may hang halfway
 through; we can't really help that. Also, some chips will be double detected;
 we choose the one with the highest confidence value in that case.
 If you found that the adapter hung after probing a certain address, you can
 specify that address to remain unprobed. That often
 includes address 0x69 (clock chip).

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
Probing for `Winbond W83697HF'
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

Do you want to scan for Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0xf411)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0xf411)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0xf411)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87591 Super IO'
  Failed! (0xf4)
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0xf4)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0xf4)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0xf4)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0xf4)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0xf4)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0xf4)
Probing for `SMSC 47M172 Super IO'
  Failed! (0xf4)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0xf4)
Probing for `VT1211 Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83687THF Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0xf4)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0xf4)
Probing for `Winbond W83L517D Super IO'
  Failed! (0xf4)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (0xf411)

Do you want to scan for secondary Super I/O sensors? (YES/no):
Probing for `ITE 8702F Super IO Sensors'
  Failed! (0xec11)
Probing for `ITE 8705F Super IO Sensors'
  Failed! (0xec11)
Probing for `ITE 8712F Super IO Sensors'
  Failed! (0xec11)
Probing for `Nat. Semi. PC87351 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87360 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87363 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87364 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87365 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Voltage Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87366 Super IO Thermal Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87372 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87373 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `Nat. Semi. PC87591 Super IO'
  Success... but not activated
Probing for `Nat. Semi. PC87371 Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC97371 Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC8739x Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PC8741x Super IO'
  Failed! (0xec)
Probing for `Nat. Semi. PCPC87427 Super IO'
  Failed! (0xec)
Probing for `SMSC 47B27x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M10x/13x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M14x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M15x/192 Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S42x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47S45x Super IO Fan Sensors'
  Failed! (0xec)
Probing for `SMSC 47M172 Super IO'
  Failed! (0xec)
Probing for `SMSC LPC47B397-NC Super IO'
  Failed! (0xec)
Probing for `VT1211 Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83627THF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83637HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83687THF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697HF Super IO Sensors'
  Failed! (0xec)
Probing for `Winbond W83697SF/UF Super IO PWM'
  Failed! (0xec)
Probing for `Winbond W83L517D Super IO'
  Failed! (0xec)
Probing for `Winbond W83627EHF/EHG Super IO Sensors'
  Failed! (0xec11)

 Sorry, no chips were detected.
 Either your sensors are not supported, or they are
 connected to an I2C bus adapter that we do not support.
 See doc/FAQ, doc/lm_sensors-FAQ.html, or
 http://www2.lm-sensors.nu/~lm78/cvs/lm_sensors2/doc/lm_sensors-FAQ.html
 (FAQ #4.24.3) for further information.
 If you find out what chips are on your board, see
 http://secure.netroedge.com/~lm78/newdrivers.html for driver status.
```

And with all those fails I knnow something must be wrong but I don't know what to do, can anyone help?

Calv

---

### Post by dcstar on 2006-10-05
> **calvinthomas said:**
> Hi, I have looked at other threads on this but they're all really old and haven't solved my problem so I thought i'd start a new thread:
.......
Use driver `**to-be-written**' for device 00:14.0: ATI Technologies Inc ATI SMBus
Probe succesfully concluded.

We will now try to load each adapter module in turn.
Load `to-be-written' (say NO if built into your kernel)? (YES/no):
FATAL: Module to_be_written not found.
Loading failed... skipping.
.......
And with all those fails I knnow something must be wrong but I don't know what to do, can anyone help?

Calv

The message seems to indicate that there is no code yet for your hardware,  it is 'to-be-written'.

You will have to wait for a kernel to support your hardware.

---

