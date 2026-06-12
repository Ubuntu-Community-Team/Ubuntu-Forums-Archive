---
title: "laptop freezes often so I have to do Alt-SysRq"
date: 2008-02-04
forum: General Help
---

### Post by pizzavortex on 2008-02-04
I have an Acer Travelmate 3012WTMi with 1.66/0.67GHz centrino duo, Intel 950 graphics, 120GB sata hdd and propietary wireless drivers. In any program, the computer can freeze completely and the only thing it responds to is Alt-SysRq.  I don't know why it crashes like this but I will be very happy if anyone can help.  :(  when it freezes I can move the mouse but i cannot interact in any way with the applications. I suspect it might be a hardware issue as my laptop is always quite hot.  perhaps it is overheating.  I tried a memtest and that worked fine.  I have reinstalled the kernel and I am going to see if that helps.

---

### Post by ayoli on 2008-02-04
you may want to try these boot options :
```
noapic nolapic acpi=off irqpoll
```
append these to your kernel line(s) in /boot/grub/menu.lst (you'll need to sudo to do that and, don't forget to do a backup before).

---

### Post by pizzavortex on 2008-02-05
What does this do?

---

### Post by ayoli on 2008-02-05
> **pizzavortex said:**
> What does this do?

It sometimes resolves boot/freeze problems, more details here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by pizzavortex on 2008-02-06
It works normally but only if acpi=off is replaced by noacpi.  I have yet to see if the computer crashes like it did.

---

### Post by pizzavortex on 2008-03-28
It still locks up.  I am constantly investigating what makes my laptop crash.  noacpi does nothing. acpi=off makes everything worse.  warsow does not work (which is a shame because i like warsow).  It may be a kernel issue because nothing works except alt-sysrq.  if i am lucky it will be fixed in hardy heron because I cannot remember anything like this when i had edgy.  :confused:

---

