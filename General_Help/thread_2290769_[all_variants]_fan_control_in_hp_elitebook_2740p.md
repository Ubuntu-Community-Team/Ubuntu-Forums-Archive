---
title: "[all variants] fan control in hp elitebook 2740p"
date: 2015-08-15
forum: General Help
---

### Post by damiano4 on 2015-08-15
Hi, I've tried to configure lm-sensors in my hp elitebook 2740p with this guide: [http://askubuntu.com/questions/22108/how-to-control-fan-speed](http://askubuntu.com/questions/22108/how-to-control-fan-speed) in order to control my fans, which are too noisy. 

sensors-detect gives me this:
```

# sensors-detect revision 6209 (2014-01-14 22:51:58 +0100)
# System: Hewlett-Packard HP EliteBook 2740p (laptop)
# Board: Hewlett-Packard 7007


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
AMD Family 16h power sensors...                             No
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


Next adapter: i915 gmbus ssc (i2c-0)
Do you want to scan it? (yes/NO/selectively): y
y


Next adapter: i915 gmbus vga (i2c-1)
Do you want to scan it? (yes/NO/selectively): Client found at address 0x58
Probing for `Analog Devices ADT7462'...                     No
Probing for `Andigilog aSC7512'...                          No


Next adapter: i915 gmbus panel (i2c-2)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: i915 gmbus dpc (i2c-3)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: i915 gmbus dpb (i2c-4)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: i915 gmbus dpd (i2c-5)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: DPDDC-A (i2c-6)
Do you want to scan it? (yes/NO/selectively): y


Next adapter: DPDDC-B (i2c-7)
Do you want to scan it? (yes/NO/selectively): y




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
loaded. You may want to run '/etc/init.d/kmod start'
to load them.


Unloading cpuid... OK
```

Then sudo pwmconfig gives me:
```
# pwmconfig revision 6166 (2013-05-01)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.


We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.



```

In windows I can easily control fan speed with hwinfo32/64, but the default settings are restored when I reboot my pc. Moreover, hwinfo doesn't work with wine. 
There was a similar thread some years ago [http://ubuntuforums.org/showthread.php?t=2121339&p=12536432&mode=linear#post12536432](http://ubuntuforums.org/showthread.php?t=2121339&p=12536432&mode=linear#post12536432) , but nobody came up with a solution. I'd be thankful for any help.

---

### Post by Frogs Hair on 2015-08-15
Hello and Welcome

I've no experience with the linked application , but it may be worth a look. I would be concerned about the reason the fan is running so fast to begin with though. I have newer elitebook and don't experience heat problems with Ubuntu or Windows. You might want take the back off and make sure the fan area is dust free. Not allowing the hardware to cool properly by controlling the fan may shorten the life of the computer.
[http://sourceforge.net/projects/fancon/](http://sourceforge.net/projects/fancon/)

---

### Post by damiano4 on 2015-08-15
@Frogs Hair: I've also tried the app you linked, but it works only if lm-sensors package can detect fans, which is exactly what doesn't work in pc. I'll try to clean fans, even if it is a well known issue that fan control is too aggressive in hp elitebook 2740p and similar models.

---

### Post by Frogs Hair on 2015-08-15
Unfortunately lm-sensors don't work on some mother boards and if you&#8217;re not noticing that the air coming is  hot , then you probably have an HP fan issue for that model.

---

