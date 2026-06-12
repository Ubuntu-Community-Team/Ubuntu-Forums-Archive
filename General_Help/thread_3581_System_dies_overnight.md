---
title: "System dies overnight"
date: 2004-11-07
forum: General Help
---

### Post by trico on 2004-11-07
Is there a mechanism in Linux that will record the reason for system failures?  

If I leave my Ubuntu system up overnight, it is consistantly locked up in the morning.  No mouse, no keyboard.  My only recourse it to force the power-off and reboot. 

I'd like to look at the error logs and see if it recorded something that could be the cause of the problem.

trico

---

### Post by az on 2004-11-07
Try /var/log

---

### Post by jdusablon on 2004-11-07
I get same result on IBM ThinkCentre. Tried disabling all power management in Ubuntu and in BIOS to no avail.

---

### Post by adamvert on 2004-11-08
[QUOTE=jdusablon]I get same result on IBM ThinkCentre. Tried disabling all power management in Ubuntu and in BIOS to no avail.[/QUOTE]
 This is perhaps the same problem I'm having with my Toshiba Satellite M30: it often just freezes up, particularly if I leave it on for a long time.  My current theory is that it's overheating, but I'm not 100% sure.

thanks,
Adam

---

### Post by trico on 2004-11-16
Mine is a tower system, no real cooling issues.  But I tried turning off the slightly exotic power management items anyway.  Did no good.

I also turned off Hypterthreading in the bios and switched to the uniprocessor kernel.  No joy.

I think its probably the graphics interface, xfree86.  But haven't figured out what to play with it.

trico

---

### Post by adamvert on 2004-11-17
[QUOTE=trico]Mine is a tower system, no real cooling issues.  But I tried turning off the slightly exotic power management items anyway.  Did no good.

I also turned off Hypterthreading in the bios and switched to the uniprocessor kernel.  No joy.

I think its probably the graphics interface, xfree86.  But haven't figured out what to play with it.

trico[/QUOTE]
 Hi Trico

In the end my problem was dodgy memory.  I had a 256 and 512 together (which is theoretically no problem), and once I removed the 256... no more freezes!

You might want to try the memory test that's on the grub menu, just in case

Adam

---

