---
title: "Setting up serial port"
date: 2016-04-29
forum: General Help
---

### Post by KeyMan123 on 2016-04-29
I run Ubuntu on an HP desktop. The system has dual hard disks, one Ubuntu the other Win-7, and dual boots using Grub. It has a serial port installed, and under Windows it shows as COM1: and works fine. Hardware address and IRQ no are exactly what you'd expect for a com port so there are certainly no hardware irregularities. In Ubuntu, there's no sign of a serial port, and if I try to start serial comms under Gtkterm or Putty, it says that TTYS0 doesn't exist. How do I set it up, please?

---

### Post by gnusci on 2016-05-01
What is the output of the following command:

$ dmesg | grep tty

---

