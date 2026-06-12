---
title: "Windows XP Login Slows"
date: 2007-08-15
forum: General Help
---

### Post by Tiger257 on 2007-08-15
Hi

I just installed Ubuntu 7.04 on my dell laptop.  I dual boot with Win XP Pro and noticed that it takes a really long time to load Windows.  Before installing Ubuntu, I would power on my computer, and select my user name in the Windows Welcome screen.  My desktop and system tray would load up in about 5 seconds, but now that I have Ubuntu, it takes roughly 30 seconds just to get past the Windows Welcome screen.  My laptop has decent hardware:

Intel Pentium M 2.00 ghz
1 gb ram
60 gb hard drive 7200 RPM

Is this something that I should expect to experience from now on because I am dual-booting?  Or is something wrong?

Thanks for your help

---

### Post by AnotherMuggle on 2007-08-15
Dual booting should have no performance impact on the other OS's.

---

### Post by insane_alien on 2007-08-15
dual booting shouldn't affect that since the operating systems have zero interaction. not sure whats going on there.

---

### Post by ddrichardson on 2007-08-15
Something is wrong. Run taskmanager and see what is eating up resources at boot. There are a number of utilities available to determine what you can load at boot and in what order.

For me it was when the windows genuine advantage update came out. Took ages.

---

### Post by kellemes on 2007-08-15
The only thing I can think of is XP hasn't enough space left for it's swapfile or something..
Did you resize it's partition maybe?

---

### Post by ddrichardson on 2007-08-15
Swapfile space wouldn't slow the initial log in process as apps are being loaded into system memory rather than being swapped out. It could simply be that the drive needs defragging.

---

