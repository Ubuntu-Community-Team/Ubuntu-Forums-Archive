---
title: "Lowering CPU fan speed"
date: 2013-02-21
forum: General Help
---

### Post by robbiedobbie on 2013-02-21
Hi,

I recently bought a computer to serve as a home server. Because of that, I decided to install Ubuntu Server. Everything is running fine. However, the sound that the cpu fan makes, is quite loud. Since the thermal readings during full load are still not too bad (43 degrees celsius), I thought that I could lower the RPM of the fan, so that it may be a bit more silent.

I searched on the internet and I found out that I had to run sensors-detect (which I already did), and I decided to run it again. The sensors it finds, are these:
```
Driver `coretemp':
  * Chip `Intel digital thermal sensor' (confidence: 9)

Driver `lm78':
  * ISA bus, address 0x290
    Chip `National Semiconductor LM78' (confidence: 6)

Driver `f71882fg':
  * ISA bus, address 0x295
    Chip `Fintek F71869A Super IO Sensors' (confidence: 9)

```

The modules are added to the /etc/modules file. However when I try to follow the next step (running pwmconfig) outputs "There are no pwm-capable sensor modules installed". Does this mean that it's not possible to control the fanspeed with this motherboard/cpu?

My motherboard is the MSI B75IA-E33 and the cpu is a Intel Celeron G1610.

Thank you in advance!

---

### Post by dino99 on 2013-02-21
linux always had (quite) ignored such settings till now, and so the kernel let the fans full speed (hope some changes coming with 3.9, as some acpi code have been reworked).

So the first thing to do is setting the best bios choices, and also using fans on 5v instead of 7/12v.  Replacing the noisy blowers by silent models is also a good idea.

note: sensors-detect is not helpfull and thread about it are quite outdated.

---

### Post by mörgæs on 2013-02-21
Does this help?
[http://ubuntuforums.org/showthread.php?t=1777887](http://ubuntuforums.org/showthread.php?t=1777887)

---

### Post by robbiedobbie on 2013-02-21
Actually I just figured it out already. I went into the bios (Didn't see it before) and found somewhere deeper in the status part an option to enable a smart fan. It's now running at 12.5% instead of 100%. When it get's hotter than 60 degrees, it will rank up until it's sufficient to cool down to under 50.

This is exactly what I wanted, it's even better than being controlled by the os. 

Thanks anywau ;)

---

### Post by mörgæs on 2013-02-21
Good, please mark the thread 'solved'.

---

