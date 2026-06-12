---
title: "SI 3112 not working after kernel upgrade"
date: 2007-03-08
forum: General Help
---

### Post by dixon on 2007-03-08
Hi,
i've upgraded to the kernel 2.6.20.1(compiled by myself using config from previous install(default ubuntu config)) and since then my PCMCIA sata controller stopped working. There'is no more /dev/sda1. Do i need to load some module or something like this?

07:00.0 RAID bus controller: Silicon Image, Inc. SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)

btw running edgy

---

### Post by ridah on 2007-03-16
I am having the same problem, with 2.6.20.3 it doesn´t load sata_sil? But if I reboot in the old 2.6.17.10 it works perfectly...

modprobe sata_sil
FATAL: Module sata_sil not found.

any ideas?

---

