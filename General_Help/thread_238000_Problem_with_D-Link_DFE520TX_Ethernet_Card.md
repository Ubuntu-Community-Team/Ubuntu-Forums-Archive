---
title: "Problem with D-Link DFE520TX Ethernet Card"
date: 2006-08-17
forum: General Help
---

### Post by freakanth on 2006-08-17
Hi,
    I recently bought a D-Link DFE520TX 10/100 Mbps Ethernet Card as the one on my motherboard had stopped working. I tried to compile and install the drivers (which were availble in the CD that was provided with the card) but it displayed an error which said

Makefile:16: *** Linux kernel source not found.  Stop.

    I downloaded the "linux-source-2.6.15" using apt-get, untared it and tried again. It still didn't work. I checked the Makefile and tried to make a few changes. Didn't help. I'm using Ubuntu Dapper Drake 6.06 (32-bit). The kernel version I'm using is 2.6.15-26-386 which was last upgraded using apt. Could someone tell me what I could do to get it to work?

Srikanth

---

### Post by philippe_carlo on 2006-08-17
Can you try 
```
sudo apt-get install linux-kernel-headers
```?

Very important.

---

### Post by yopnono on 2006-08-17
> **freakanth said:**
> Hi,
    I recently bought a D-Link DFE520TX 10/100 Mbps Ethernet Card as the one on my motherboard had stopped working. I tried to compile and install the drivers (which were availble in the CD that was provided with the card) but it displayed an error which said

Makefile:16: *** Linux kernel source not found.  Stop.

    I downloaded the "linux-source-2.6.15" using apt-get, untared it and tried again. It still didn't work. I checked the Makefile and tried to make a few changes. Didn't help. I'm using Ubuntu Dapper Drake 6.06 (32-bit). The kernel version I'm using is 2.6.15-26-386 which was last upgraded using apt. Could someone tell me what I could do to get it to work?

Srikanth

It this card not using realtek or atheros? if so ubuntu should "see" the card and you should be able to use the native drivers for it.

---

### Post by freakanth on 2006-08-17
I already have the kernel headers installed. And the native drivers aren't working either :sad: .

---

