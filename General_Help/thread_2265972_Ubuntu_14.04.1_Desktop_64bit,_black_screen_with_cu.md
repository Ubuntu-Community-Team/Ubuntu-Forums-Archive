---
title: "Ubuntu 14.04.1 Desktop 64bit, black screen with cursor after Grub screen."
date: 2015-02-18
forum: General Help
---

### Post by Tech0 on 2015-02-18
My computer has been running for several days and has become unresponsive.
After a hard shutdown and restart, the computer loads into a black screen with a blinking cursor, which did not respond to any keyboard action.
Another hard shutdown and restart, it loaded into the Grub screen where I selected *Ubuntu, and it loaded the same black screen.
Another hard shutdown and restart, clicked "e" on *Ubuntu and removed parameters "quiet" & "splash" & set GFXMODE to "text", clicked "Ctrl+x" to load boot messages. The readout stops after these lines:

[  0.576698] ehci-pci 0000:00:1d.7: debug port 1
[  0.580639] ehci-pci 0000:00:1d.7: irq 23, io mem 0xfe7ff800

What does this mean? And what more diagnostics can I do to find out the problem?

---

