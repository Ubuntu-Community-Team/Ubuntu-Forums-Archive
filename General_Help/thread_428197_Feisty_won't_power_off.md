---
title: "Feisty won't power off"
date: 2007-04-30
forum: General Help
---

### Post by riscbroker on 2007-04-30
I installed Feisty as a dual boot option on an ancient Celeron, when I quit the OS the display shows Ubuntu shutting down (the graphic bar diminishing), but the system does not power off automatically, I have to hit the power button on the case.  Any hints please??

---

### Post by ceno-byte on 2007-04-30
hello there riscbroker try this:

open the terminal and type: ```
sudo gedit /boot/grub/menu.lst
``` and look for something like this 

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic 
root=UUID=07433100-7251-4959-8201-98f492b3ad24 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault



just add acpi=force to this line : kernel		/boot/vmlinuz-2.6.20-15-generic acpi=force 

that should fix your problem

---

### Post by riscbroker on 2007-04-30
Hey Ceno-Byte, thanks for this info, works beautifully.

I've had a bunch of distros on this machine up to now - Knoppix, Mepis, DSL, Kubuntu, Ubuntu  6.06 and now Feisty - this is the dog's bo$$ocks

---

### Post by ceno-byte on 2007-04-30
well glad to have been able to help you riscbroker :)

---

### Post by Xiphias88 on 2007-05-03
Hi,

I'm running Feisty and was running Edgy, and this issue was present in both for me.

Unfortunately, this solution mentioned above doesn't work for me (my mobo bios only supports ACPI - so no APM, and is new enough that ACPI isn't automatically blocked by the y2k blacklisting.

I have tried both forcing APM and ACPI (not simultaneously) and still can't get my system to auto power off.

Attached is a copy of my dmesg output as it stands. Any help here would be greatly appreciated.

---

### Post by _pitch on 2007-05-17
I've got the same problem...
I also tried to force acpi and amp.
I also tried to set my bios to enable acpi 2.0 on my mobo, ASUS P5B-V, but without success.
Which version of acpi is supported in Linux kernel? As I've read acpi is in version 3.0 now, or..?
/_pitch

---

### Post by chewjoel on 2007-05-17
It doesnt works on mine.
Mine is a ASUS M2400N laptop, using Feisty.
Seems quite a couple of problem with this labtop to work with Feisty and Edgy: Sound Card, Power Off, Hibernate, and my gaim would be killed every now and then, all by sudden.

---

### Post by Neobuntu on 2007-05-30
```
# defoptions=quiet splash acpi=force
```...is where you probably want to put it and then...```
sudo update-grub
```

Still, mine does NOT work, either. 

Why would this no longer work? It actually DID work a few Kubuntu releases back on this same hardware.

Strange. What's going on?

---

### Post by timothy_duncan on 2007-07-24
got the same problem but the solution doesnt work for me.  i was using kubuntu dapper before and my computer would turn off automatically.  now that i completely installed ubuntu feisty, my computer won't turn off automatically

---

