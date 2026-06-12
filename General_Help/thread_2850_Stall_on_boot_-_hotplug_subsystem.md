---
title: "Stall on boot - hotplug subsystem"
date: 2004-11-01
forum: General Help
---

### Post by tuxx on 2004-11-01
Hello

Ubuntu 4.10 is giving me greefs. I love the system but on boot it stalls sometimes.

If I have all 6 USB ports enabled in BIOS it stalls on 50-75% of the times and I have to reset my computer. The 2 of the 6 ports are the ones internally on the mobo.

If I disable those 2 and then have only 4 enabled it stalls on perhaps 20% if at all - so that's better but still really really annoying and devestating for the system.

Fiddling with the USB legacy support makes no difference.

I have the latest BIOS.

My hardware specs can be seen here: [http://tuxx.dk/computers.htm#portrica](http://tuxx.dk/computers.htm#portrica)

How do I fix that?

---

### Post by tuxx on 2004-11-01
Hmm I believe my problem is solved.

I have in my keyboard an USB-hub. I've now disconnected the cord to that hub and now it's booted ~6 times perfectly - before that it was the other way around, maybe 2 times out of 6 if I were really lucky.

---

### Post by Magneto on 2004-11-01
[QUOTE=tuxx]Hmm I believe my problem is solved.

I have in my keyboard an USB-hub. I've now disconnected the cord to that hub and now it's booted ~6 times perfectly - before that it was the other way around, maybe 2 times out of 6 if I were really lucky.[/QUOTE]

Have you tried reconfiguring your kernel? Try playing with the three usb options uhci ohci ehci in the kernel, I'd bet that if your hardware is sound the issue is using one of those options incorrectly.

---

### Post by jdong on 2004-11-01
try booting with **idle=poll**. If you have "disable legacy USB support" or a similar option in your BIOS, make sure legacy USB is off.

---

### Post by tuxx on 2004-11-01
[QUOTE=Magneto]Have you tried reconfiguring your kernel? Try playing with the three usb options uhci ohci ehci in the kernel, I'd bet that if your hardware is sound the issue is using one of those options incorrectly.[/QUOTE]

No I haven't tried that. I don't know how to fiddle with kernels and my worst nightmare would be a system totally screwed because I did something wrong with the kernel.

---

### Post by tuxx on 2004-11-01
[QUOTE=jdong]try booting with **idle=poll**. If you have "disable legacy USB support" or a similar option in your BIOS, make sure legacy USB is off.[/QUOTE]

USB Legacy support has been well tested on both on/off.

Where do I pass the idle-poll ?

---

