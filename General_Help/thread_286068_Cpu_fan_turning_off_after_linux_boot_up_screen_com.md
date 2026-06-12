---
title: "Cpu fan turning off after linux boot up screen comes up"
date: 2006-10-27
forum: General Help
---

### Post by gearshifter on 2006-10-27
I have quite a weird problem.  My computer's fan is turning off after leaving grub and when its in the boot screen.  It works in bios and everywhere else but then immediately shuts off and is causing my computer to overheat.

I was going to try another slot for the fan to plug in, but to no avail, there is no other port i can use.  

This is A desktop, with a Celeron/Intel motherboard combo with integrated graphics.  

Any way i can fix this?


Thanks,
Jason

---

### Post by gearshifter on 2006-10-27
I have done some tests and found that the cpu fan comes on for the Dapper Kernel but will stay off for the edgy kernel.  Sadly, Ndiswrapper and such aren't working for the previous kernel for me and I want a fix for edgy :(


Is there a way to make all fan control go away?

Thanks,
Jason

---

### Post by Eversmann on 2006-11-05
Thanks for the reply, i've searched and searched on the forum about this, but  seems there were some problems with the word "fan" or something like that, i didn't find those post.

I'll post in those threads.

---

### Post by neza.ics on 2006-11-10
Hey guys, im having the same problem in edgy.  It only happens with ubuntu.  any other distro is fine.

Machine specs..
Emachines T2042
CPU: Intel® Celeron® Processor 2GHz (w/128KB L2 cache & 400MHz FSB)
Operating System: Ubuntu 6.10
Chipset: Intel® 845GL chipset
Memory: 256MB DDR (P2100)
Hard Drive: 40GB HDD
Optical Drive: 40 × 12x40 Max. CD-RW Drive; 16x Max. DVD Drive; 3.5" 1.44MB FDD
Video: ATI Radeon 7000/VE
Sound: AC '97 Audio
Network: 10/100Mbps built-in Ethernet
Modem: 56K ITU v.92-ready Fax/Modem

---

### Post by neza.ics on 2006-11-10
Hey guys, i found a temp workaround.  When you boot into the install cd, make a boot option acpi=off.  That seems to keep the fan on through the install.  Im not sure if it will stick after.  hope that helps.

---

### Post by neza.ics on 2006-11-10
Ok so after the install the setting doesn't stick.  Once you boot you can edit the grub menu to add the line acpi=off.  

sudo gedit /boot/grub/menu.lst

then add acpi=off to the end of

kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash acpi=off

hope this helps.

---

### Post by Tobster on 2006-11-10
Guys,

When was the last time you clean your CPU?

I bet they are really dirty so dirty that the fan can't move.

The OS does not control the fan as it is an automatic response when you turn the power on

---

### Post by neza.ics on 2006-11-10
trust me Tobster, my pc is clean.  I clean it out about every two months.  This is not a hardware problem.  The fan used to work fine, before i upgraded to Edgy.

---

