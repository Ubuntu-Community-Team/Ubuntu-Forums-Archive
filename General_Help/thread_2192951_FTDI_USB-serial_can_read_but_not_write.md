---
title: "FTDI USB-serial can read but not write"
date: 2013-12-10
forum: General Help
---

### Post by marlon_smith on 2013-12-10
Hi everyone,

This worked fine in Ubuntu 11.10, but is not working in 12.04. I'm using an FTDI USB-serial chip in a custom hardware product, and connecting to it via Cutecom to send simple text data back and forth. This worked properly in 11.10, but in 12.04 my PC can receive data from the FTDI chip, but it can't send data to the chip.

Here's what I've tried:

I've added my user to the dialout group
I've tried starting Cutecom with sudo
 I've also tried minicom and GTKterm
 I've also tried using GTKterm to toggle the DTR line so it's low
I've also tried running stty on my working copy of 11.10 and then using the exact settings in 12.04

If anyone has any ideas, I'd really appreciate the help. Under pressure to get this project working.

Thanks

Marlon

---

### Post by marlon_smith on 2013-12-10
Apologies everyone, it was an issue with my hardware.

---

