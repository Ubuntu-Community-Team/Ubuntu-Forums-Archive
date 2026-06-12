---
title: "[SOLVED] ACPI Suspend not working on Intel G33-based motherboard"
date: 2007-10-30
forum: General Help
---

### Post by sebrock on 2007-10-30
I recently bought a new mainboard: Gigabyte GA-G33M-S2H which according to specification has ACPI 1.0b. I cannot however suspend correctly. The computer shuts down fast and fine, but upon resume nothing happens (except power-on). At least not that I can figure out. I do not get a screen picture nor can I ping the machine.

mainboard uses the Intel G33 chipset.

:confused::confused:

EDIT: I now am able to do a suspend to RAM. However, when I reboot I have to go into tty1 or so. And this message is constantly flooding the syslog:

printk: 39 messages surpressed
Buffer I/O on device sr0

Also, LAN is totally down. Cannot even be restarted.

---

### Post by sebrock on 2007-10-30
Attached is my kern.log as it shows during suspension and wakeup.

I noticed that I acutally can do this, but screen stays blank until I change TTY to 1 and then back to 7 using Alt+Ctrl+1 (7).

But of cause almost everthing is dead when it wakes up.

---

### Post by sebrock on 2007-11-04
bump

---

### Post by sebrock on 2008-07-18
works with Hardy

---

