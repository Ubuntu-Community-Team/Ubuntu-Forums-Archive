---
title: "Since the last update I cannot run my Ubuntu 14.04 from my laptop. What should I do?"
date: 2015-12-17
forum: General Help
---

### Post by Mikael_Pratama on 2015-12-17
I have recently update my Ubuntu 14.04 in my laptop (Lenovo Z580). When I boot the Ubuntu logo with five dots below it appeared and then it goes into black screen. Nothing will happen for any keyboard and mouse button I pressed. However, when I pressed my laptop power button the Ubuntu logo appeared again before my laptop turned off. I have tried to use the second option (the save boot I think) to boot into my Ubuntu, after there is a console message about loading the operating system into RAMDISK, it goes the same, get the Ubuntu logo and then black screen.

What should I do?
How I can I copy my data from the Ubuntu into Windows7 (dual boot)?

---

### Post by QIII on 2015-12-17
Hello!

What is the manufacturer and model of your graphics adapter?  Were you running a proprietary driver?  How did you install it?  Did the update include an updated kernel?

---

### Post by Mikael_Pratama on 2015-12-17
The graphic adapter is NVIDIA GT630M.
I think last time I change the driver into the proprietary (honestly, I am not sure what you meant by proprietary driver here, but it is definitely not the open source one).
I install the update from the automatic updater that then asked me to restart my computer.
I do not know what kernel is, so I am not sure. But it is the latest update around yesterday or so.

---

### Post by Bashing-om on 2015-12-17
Mikael_Pratama; Hello ;

A broken proprietary ( Non-ubuntu ) graphic's driver is likely .
To isolate; can you boot an older kernel from grub's boot menu ?

Or perhaps boot the system with the " nomodeset "  boot parameter ?

[INDENT][INDENT]all in the process
[INDENT][INDENT][INDENT]where is it failing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Mikael_Pratama on 2015-12-17
Hey I have used all older kernel options. All of it have the same issue. At this moment I have secured my data and re - installing the whole operating system.

---

