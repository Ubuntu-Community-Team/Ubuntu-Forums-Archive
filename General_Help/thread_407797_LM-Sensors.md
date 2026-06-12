---
title: "LM-Sensors"
date: 2007-04-12
forum: General Help
---

### Post by celticbhoy on 2007-04-12
cant get LM-Sensors to work. followed how to but get output from sensors command as :-

Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!


I want to overclock the system. but not without being able to check on temps.

what do I do now ?????

---

### Post by Gillingham on 2007-04-12
You need to do some more steps.  Look at [this how to]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/Hardware#How_to_detect_CPU_temperature.2C_fan_speeds_and_voltages_.28lm-sensors.29") from the ubutnu guide.

---

### Post by celticbhoy on 2007-04-12
Nope, still getting the same.

Are the files mentioned nedding updated or something - maybe missing ????

---

### Post by Gillingham on 2007-04-13
Ok - I can't help with LM-sensors, that how to got LM-sensors working for me.  

Have you tried other methods of getting the cpu temperature?  In gnome you can add a "hardware sensor monitor" via the add to panel menu or there is GKrellM (which has the advantage of actually seeing the temperature of my graphics card).

Good luck

---

### Post by celticbhoy on 2007-04-14
GKrellM seems to do the job but the system monitor only gives usage not temps

---

### Post by celticbhoy on 2007-04-14
GKrellM seems to work but the option for temp & voltage is not allowing me to enable.

is there a setup for this app ????

---

### Post by celticbhoy on 2007-04-14
just checked it uses lm-sensors for its temp & voltage info.

So still stuck with getting lm-sensors to work.

---

### Post by Gillingham on 2007-04-14
Ok I hadn't realized that - I'm sure I had it working before I got LM-sensors working.

By the way I wasn't thinking of the system monitor, I have an option called hardware sensor montior, which has an extra temperature gauge over Lm-sensors, so hopefully it isn't totally dependent on LM-sensors. 

A thought has just occurred to me - I seem to remember that LM-sensors doesn't support all motherboards have you checked yours with the LM-sensors webpage?

---

### Post by celticbhoy on 2007-04-14
will give it a look

---

### Post by deodatus on 2007-04-14
I'm having the same error message:
> Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

---

### Post by Tanker Bob on 2007-04-14
Exactly the same error here.  I've been through the HOWTO.  I'm using an MSI P6N SLI Platinum motherboard.

---

### Post by energiya on 2007-04-14
You have to recompile the kernel and include I2C support.
> 
Code maturity level options
  [*] Prompt for development and/or incomplete code/drivers

Bus options (PCI, PCMCIA, EISA, MCA, ISA)
  [*] PCI support

Device Drivers
    I2C support
      <M> I2C support
      <M> I2C device interface
      I2C Algorithms
        <M> (configure all of them as modules)
      I2C Hardware Bus support
        <M> (configure all of them as modules)
      I2C Hardware Sensors Chip support (up to 2.6.13-rc2)
        <M> (configure all of them as modules)
    Hardware Monitoring support (since 2.6.13-rc3)
      <M> (configure all of them as modules)

([http://www.lm-sensors.org/wiki/Kernel2.6](http://www.lm-sensors.org/wiki/Kernel2.6))
I have managed to install it on every kernel version I have tried, included 2.6.20

---

