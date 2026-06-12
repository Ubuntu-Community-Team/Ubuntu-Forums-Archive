---
title: "System suddenly unresponsive yet top/free show plenty of resources available?"
date: 2014-12-22
forum: General Help
---

### Post by r0d3nt on 2014-12-22
Hi All,

I was zero wiping a 2TB external USB drive using ddrescure -f /dev/zero /dev/sdc on a 64-bit Ubuntu 14.10 installed on an ssd.  The external drive had been problematic, so I thought giving it a full wipe might help with determining what the problem might be.  smartctl had already uncovered that the drive had plenty of already reallocated sectors and that there were more pending sectors waiting.  I was also running a long smartctl test against the drive just to be thorough.

What is particularly odd though is that the whole time I was doing all of this, I initially had chrome open to my usual 20-ish tabs open [I know that's a lot and very resource intensive, but that's just how I roll], and had turned off the power management so that the wiping/testing could run uninterrupted.  I also had xscreensaver running, but I decided to disable it during the testing as well.  This is when things started to get weird.  I run Mate and have a shortcut to the xscreensaver-demo program so I can settings.  Every time I tried to launch the program, it just wouldn't respond [which it would normally].  Then X Windows/Mate seemed to freeze up entirely.  When the system decided to catch up with itself, I was able to quit out of my 20 tab chrome, and the system then became a bit more responsive.  Even though with chrome closed the system still wasn't behaving quite right.  Running top didn't show and major resources being used up nor did free show that there wasn't much RAM being utilized in cache.  I could only surmise that the ddrescue was doing a very low level, resource intensive task that was bogging the whole system down.  As soon as the ddrescue finished [some 20 hours later] is when the system came fully back to life.

My question is, how can I more accurately gauge where the system bottleneck was?  top didn't help, nor did referring to free or any of the graphical tools to display what system resource were used/available.  The system is a bit older with I think 1.5Gb sata connections with USB 2.0 for the external hard drive connection.  Again, I can only assume that the bandwidth of the sata/USB bus is what caused things to slow down so greatly, but I'd really like to see some proof of this.

Does anyone know what tools I could use for this or what other metrics I could refer to in figuring this out?

-Ubence

---

### Post by mcduck on 2014-12-22
Since you were using top to check resources, you could have checked the value for iowait  ("%wa" in top, the time the processor is stalled waiting for data from some hardware device. Usually waiting for the hard drive). As you suspected, the reason for unresponsiveness was most likely result of the disc access, which of course can't be solved by CPU power or by suing RAM, so you wouldn't notice anything if just looking at normal CPU usage values or free memory...

Load values can also  be useful, since they include io wait, hardware & software interrupts and other reasons why the CPU might be busy doing nothing at all.

Of course there's also *iotop* which could be useful tool for this kind of stuff as well, although in this case you already knew that you were running ddrescue.

Anyway, USB is fairly slow, and also depends on CPU  to deal with data transfers (unlike, say, SATA or Firewire), so I'd guess a nice combination of iowait and hardware interrupts caused by lots of IO on a USB-connected drive.

---

