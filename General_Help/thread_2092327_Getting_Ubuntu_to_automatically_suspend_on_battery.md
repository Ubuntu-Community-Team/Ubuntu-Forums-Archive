---
title: "Getting Ubuntu to automatically suspend on battery low (command-line)"
date: 2012-12-07
forum: General Help
---

### Post by whitecat23 on 2012-12-07
I've been using Ubuntu without a desktop environment on one of my computers  - just pure command-line without even an X server installed. I need to keep it this way. What surprises - completely throws me - is that there is very little to no automatic power management going on; I need the computer to automatically and gracefully power off or hibernate when the laptop battery reaches a critically low level. Instead, the machine abruptly shuts down and causes filesystem corruption every time.
How is it that there is no official Linux (or even Ubuntu- specific) power management driver that works in or out of a graphical session? Windows handles handles events like this seamlessly by hibernating... but c'mon, do I really need to run a desktop under Linux to get the full benefits of automatic power management? If so, this should be treated as a bug or serious deficiency.
How can I get Ubuntu 12.04 and up to automatically shut down gracefully from the command line? The solution cannot conflict with desktop power managers, since I use another computer with X, but spend a lot of time there in pure command-line too.

---

### Post by Isamu715 on 2012-12-08
Take a look at *laptop-mode-tools*. It's a power-saving solution that doesn't require any graphical DE. There's an option to auto-hibernate on low battery in */etc/laptop-mode/conf.d/auto-hibernate.conf*. An option to shut down should be in one of LMT config files(in */etc/laptop-mode/*). If not you can change the hibernate command in *auto-hibernate.conf *to a shutdown command.

---

### Post by whitecat23 on 2012-12-10
Thanks. I shall try that!

---

