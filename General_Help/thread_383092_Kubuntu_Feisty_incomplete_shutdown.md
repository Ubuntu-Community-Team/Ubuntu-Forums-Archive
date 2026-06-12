---
title: "Kubuntu Feisty incomplete shutdown"
date: 2007-03-12
forum: General Help
---

### Post by AstronomyDomine on 2007-03-12
I'm running Feisty Herd 5, with all of the latest updates. I've just switched over from Slackware and have never had any problems.

At first, most of the time, when I used KDE to shut down or restart the computer, it would begin to shut down, then it would hang at a black screen until I manually rebooted it. However, if I manually ran init 0 or init 6, the computer usually would shut down or reboot correctly. 

I did some research and found that ACPI could be the problem. I disabled it by adding acpi=off to my grub kernel line. That did not help the problem at all. After doing some more research, I added apm=power_off to my kernel line. That also did not help. It actually seemed to make things worse, as even running init myself would not shut down the computer completely.

I also attempted to turn off ACPI and AMP in the BIOS, this also had no affect.


Any ideas?

---

### Post by AstronomyDomine on 2007-03-14
Anybody have any ideas? It's beginning to cause problems as my file systems will not unmount, and having to power off the computer with them mounted is causing corruption.

---

### Post by KStorm on 2007-03-17
One thing I found that helped (with Kubuntu Feisty) was to edit /etc/kde3/kdm/kdmrc by uncommenting the line that says "TerminateServer=true" (about 4/5 of the way down).  After one restart, I was able to reboot without manual shutdown.

---

### Post by Haim on 2007-03-20
if you're using APM then this should help, worked for me.

[http://www.togaware.com/linux/survivor/APM_Power.html](http://www.togaware.com/linux/survivor/APM_Power.html)

Note that ubuntu uses apm as a module.

---

