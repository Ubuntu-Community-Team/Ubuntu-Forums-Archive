---
title: "Ascii serial link to external devive"
date: 2024-06-13
forum: General Help
---

### Post by docstafford on 2024-06-13
My extensive experience  as an AT&T engineer 26 years ago in Unix system hardware and software devrlopment is too long dormant to help me with my current problem, especily in light of difference between unix and ubuntu.
I am using Ubuntu 24... on an HP laptop very successfully. I am trying to revive an old AT&T 3b2 computer that used an rs232 serial interface on the console port. The hardware interface is not the problem as I can find a usb to rs232 hardware. Serial After too much diatribe my question is: how can I get my linux machine to act as a dumb terminal (no gui, etc).
Relays forever!

---

### Post by currentshaft on 2024-06-13
The serial connection is something usually enabled in BIOS/firmware settings. To connect, use a program like minicom. Unless I've misunderstood what you're trying to do?

---

### Post by docstafford on 2024-06-13
Best regards and thanks for reply. I want to connect a (possibly dead) computer to one of my usb ports and be able to use my laptop as a terminal (with keyboard) be be able to "talk to" that device. That device is an old AT&T 3b2 computer (likely before your time). External connection to that device was through a "console" rs232 port using RJ 45 connection. I have worked out all the pin outs  but just need to emulate a dumb terminal. I had a couple of dumb terminals that would normally be used but they both smoked after I cleaned them up and applied power. My level of concern for getting either of those terminals running is not high given the likelihood that I should be able to get a virtual termnal setup going. All of these devices have been sitting for 25 years in a not too clean environment.

---

### Post by HermanAB on 2024-06-13
There is a nice terminal program called cutecom.

Make sure that you are a member of the dialout group.

The USB serial devices have names like /dev/ttyUSB0

More low level info here:
https://www.aeronetworks.ca/2014/10/serial-ports-revisited.html?m=1

---

