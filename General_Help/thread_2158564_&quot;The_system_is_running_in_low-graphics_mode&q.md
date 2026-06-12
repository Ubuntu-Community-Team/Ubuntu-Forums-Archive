---
title: "&quot;The system is running in low-graphics mode&quot;"
date: 2013-06-29
forum: General Help
---

### Post by Janno2 on 2013-06-29
All of a sudden my Ubuntu 13.04 does not boot anymore. If powering-up the laptop I get the message: "The system is running in low graphics mode". Hitting OK gives me a new screen, where I should be able to select a next step. However, nothing is working, all I can do is pressing the power-key in order to shut down the system.

So I serched for help, and found that pressing and holding the SHIFT-key, and powering-up the system again, makes GRUB to come up.
There I do select "Advanced options for Ubuntu", and get a new screen where I can select from: A: Ubuntu, with Linux 3.8.0-25-generic, B: Ubuntu, with Linux 3.8.0-25-generic (Recovery mode), C: Ubuntu, with Linux 3.5.0-31-generic, and D: Ubuntu with Linux 3.5.0-generic (Recovery mode).

If selecting option C (Ubuntu, with Linux 3.5.0-31-generic), I get a new srcreen with "Loading Linux 3.5.0-31-generic...", followed by
"loading from initial RAM-disk...".

And after some waiting my Ubuntu-desktop is there, up and running.

The question, of course, is why it is no longer possible to use Ubuntu in the default high resolution from booting?

---

### Post by grahammechanical on 2013-06-29
When you select option C and you get to a desktop, is it in low resolution mode? That is not clear from your post. Unless there are typing errors option C is giving you a newer kernel than option A. Kernel 3.8.0-31 for option C but only 3.8.0-25 for option A. It is usually the other way around

Next time at Recovery Mode select Grub  -  update grub boot loader. See if that improves things. Have you tried Recovery mode>Resume. If you are getting to a desktop go to system settings>software & updates>additional drivers tab and experiment with video drivers.

Regards.

---

