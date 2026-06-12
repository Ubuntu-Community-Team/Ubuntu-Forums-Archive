---
title: "How to detect CPU temperature, fan speeds and voltages (lm-sensors)"
date: 2006-10-29
forum: General Help
---

### Post by wd3thatsme on 2006-10-29
ok i followed how to detect cpu temp, fans speeds.etc half way down edgy starter guide



 Now follows a summary of the probes I have just done.
 Just press ENTER to continue: 

Driver `w83627ehf' (should be inserted):
  Detects correctly:
  * ISA bus address 0x0290 (Busdriver `i2c-isa')
    Chip `Winbond W83627EHF/EHG Super IO Sensors' (confidence: 9)


I will now generate the commands needed to load the I2C modules.

To make the sensors modules behave correctly, add these lines to
/etc/modules:

#----cut here----
# I2C adapter drivers
i2c-isa
# I2C chip drivers
w83627ehf
#----cut here----

Do you want to add these lines to /etc/modules automatically? (yes/NO)y
wd@linuxbox:~$ sensors -s
Can't access procfs/sysfs file
Unable to find i2c bus information;
For 2.6 kernels, make sure you have mounted sysfs and libsensors
was compiled with sysfs support!
For older kernels, make sure you have done 'modprobe i2c-proc'!

---

### Post by ~LoKe on 2006-10-29
I get the same problem.

---

### Post by wd3thatsme on 2006-10-29
this is really getting me down because i really want to use gkreallm's monitoring feature. so far everything else is going ok. i've been hearing alot of 64bit nightmares. if u find a solution pleas post it here for me.

---

### Post by ~LoKe on 2006-10-29
Conky seems to still be able to get my temps, as well as GKrellM.

---

### Post by wd3thatsme on 2006-10-29
wait....don't u have to install the sensor into the kernel first? u mean i'm doing all this for nothing? i can just install conky or gkrellm and it will automatically pick up sensors for my fans, cpu etc.....

---

### Post by ~LoKe on 2006-10-29
> **wd3thatsme said:**
> wait....don't u have to install the sensor into the kernel first? u mean i'm doing all this for nothing? i can just install conky or gkrellm and it will automatically pick up sensors for my fans, cpu etc.....

Seems that way.

---

### Post by wd3thatsme on 2006-10-29
can i copy ur conky log file to set my sensors?

---

### Post by ~LoKe on 2006-10-29
> **wd3thatsme said:**
> can i copy ur conky log file to set my sensors?

I've changed my conky configuration and thus lost my temps.  I'll see if I can get them back up tomorrow.

---

### Post by wd3thatsme on 2006-10-29
hey thanks. i just used synaptic to get conky so i'll do some reading and see what i can do..

---

