---
title: "System freezing over weekend"
date: 2015-02-16
forum: General Help
---

### Post by grapnell-gmail on 2015-02-16
Hi all,

I am having an issue that has happened to me twice now in the last two weeks. I've left my Ubuntu desktop running over the weekend, only to come back to find it completely frozen. The screen is black, and even the Magic SysRq sequence won't unfreeze it. I have to do a hard reset. I have checked the dmesg and syslog, and can't find anything. Syslog shows everything running up to Feb 13, then all of a sudden, nothing. No error message or anything, until I hard reboot on this morning, then syslog picks up from Feb 16. Is there a log I can check that may give me more information on perhaps a hardware issue that may be going on here? This computer has run perfectly fine for over a year now with no issues, this just started happening two weeks ago, and I don't like doing hard resets. It's not going into suspend or hibernate, all of that is disabled. My hardware specs are Intel I7 processor, 64 GB Ram, 2 TB HD (barely 1/4 full). I like to leave it running over the weekend so I can SSH into it if I need to, as it is a work computer.

Thanks for any guidance, let me know if I need to post any logs or other info.

---

### Post by ajgreeny on 2015-02-16
It could be power-supply-unit, memory or many other hardware faults, or it could, of course, be a software problem following an update.

Which version are you running?
Trusty 14.04 had a new kernel recently, 3.13.0-45, which could be causing problems, though it runs fine on my Intel i5, but it might be worth booting to a previous kernel to test that possibility.

You could also run memtest from grub, overnight if possible, to test your memory. Unfortunately I don't know any simple way to test a power-supply-unit.

---

### Post by tgalati4 on 2015-02-16
If you don't find anything in /var/log, then I would suspect the PSU as ajgreeny suggested.  Buy a new one with a return policy or grab one from another machine and run it for a while.  Check for bulging or leaking capacitors on the motherboard.

---

### Post by grapnell-gmail on 2015-02-23
Thanks, it does appear to be the PSU. I've replaced it and it hasn't happened since.

---

### Post by tgalati4 on 2015-02-23
You were lucky.  Many times a failing power supply will damage the motherboard resulting in a no-boot condition.  I am glad that you got it figured out.

---

