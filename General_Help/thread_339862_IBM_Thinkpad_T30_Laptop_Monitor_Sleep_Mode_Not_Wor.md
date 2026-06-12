---
title: "IBM Thinkpad T30 Laptop Monitor Sleep Mode Not Working"
date: 2007-01-16
forum: General Help
---

### Post by pak33m on 2007-01-16
Hello,

Usually I notice my monitor on my IBM Thinkpad T30 laptop go into sleep mode as I work away on my desktop. Lately I have noticed that the screen just flashes for a quick second, at least every 10 minutes, like it is trying to go to sleep. 

In that last few weeks I have been booting into a 686 kernel without realizing it. I'm not sure how this happened, but as of yesterday I commented out the 686 lines in the grub to boot to the 386 kernel by default 

I am thinking that this sleep problem is a result of running with the 686 kernel. However, the problem is still happening today, even after booting into the 386 kernel. Before I made the boot change though the screen would act the same as listed above, but the entire laptop would lockup!

Any help would be appreciated.

---

### Post by gapplewagen on 2007-01-16
Have you made any changes to X lately?  When I use fglrx driver I have issues with sleep.  I'm on a HP Compaq nx7000 though.  Also could be something ACPI related if you have changed/updated anything.

---

### Post by pak33m on 2007-01-16
At one time several months ago I tried to get Beryl working on my laptop, but sleep mode has been working since then.

I am not sure where to start troubleshooting acpi.  I did notice in the System Log that acpi was disabled.  I believe it has been that way since the install!?

---

