---
title: "Teamspeak + Urban Terror == Mouse lockout"
date: 2007-07-21
forum: General Help
---

### Post by FRuMMaGe on 2007-07-21
When I try and run Urban Terror 4.0 when I am running Teamspeak, the Urban Terror windows flashes for about half a second, then reverts to desktop.  What's more, my mouse gets completely locked out and all I can do is restart the xserver (Ctrl+Alt+Backspace).

What could be wrong?

---

### Post by FRuMMaGe on 2007-07-21
bump :(

---

### Post by geraldm on 2007-07-21
Details?  What messages are in the file syslog when the mouse dies?  
Is there a disconnect message in syslog for either the mouse, or a hub?
Is the mouse convertible usb|PS/2?  If so, which was in use?
Does your motherboard + usb port card(s) have UHCI, OHCI, BOTH hardware?

Look for incorrect interrupt assignments for USB hardware, especially ohci_hcd uhci_hcd
in /proc/interrupts
Possible solution (does not work everywhere), use only if you have a usb device disconnecting,
and your log file suggests this: 
when booting, in the kernel options line, add the parameter "irqpoll"

Gerald

---

### Post by flogee on 2008-01-28
ive got the same problem, after about 10min gameplay the scree flashes and i the game gets windowed (not fullscreen) from there i cannot control my mouse, and have to restart x server

but im not using teamspeak

---

### Post by Istonian on 2008-02-07
bump because I am now having the same problem. Gets annoying after a while.

---

