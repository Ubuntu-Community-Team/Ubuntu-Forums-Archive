---
title: "Try to shutdown, machine reboots instead??"
date: 2014-11-08
forum: General Help
---

### Post by dewdrop_world on 2014-11-08
Hi,

I'm finding that, more often than not, trying to shut down my machine (a ThinkPad Edge E341) actually causes the machine to reboot. I discovered this the hard way when my machine was totally out of battery after a flight. I had asked the machine to shut down, and then closed the lid, assuming that it would really shut down. Instead, it rebooted, and ran on full power (with the lid closed) until the battery died.

Since then, I've observed the behavior repeatedly.

I'm using Gnome-shell 3.4.1. There's no shutdown option in the user account menu -- instead, you press and release the power button, which brings up a dialog box with options to cancel, shutdown or restart. Clicking shutdown here causes a reboot. I also tried logging out (back to the Ubuntu login screen) and shutting down from the power-icon menu. That worked once or twice, I think, but today I saw a reboot even from there. I was not in a gnome-shell session at that time, so it couldn't be purely a gnome-shell issue.

My last test was "sudo shutdown now -P" at the command line. The system *did* shutdown properly. So I think the underlying shutdown mechanism is fine, but the GUI is issuing the wrong command to the system.

How do I fix this?

$ uname -a
Linux hjh-e431 3.11.0-26-generic #45~precise1-Ubuntu SMP Tue Jul 15 04:02:35 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Thanks in advance,
hjh

---

