---
title: "Monitor mode not supported????"
date: 2007-06-22
forum: General Help
---

### Post by nooor7772000 on 2007-06-22
hi

when i open my terminal and use commands it say:-



Interface       Chipset         Driver

1.2.0kmprq
Monitor mode not supported, please upgrade


what that mean and how fix it please??
thanks

---

### Post by georgiabiker on 2007-06-28
Here's what it means.

1. You are trying to crack a WEP encryption on someone's wifi.

2. Whoops! Your wireless card doesn't support "monitor" mode. It is probably currently in "managed" mode.

3. Too bad, so sad, love, dad.

---

### Post by nooor7772000 on 2007-06-29
so so sweet thanks.............

for that reply i realy with no lies ..lol cracking wep ..........so what can i do for that...........................

---

### Post by georgiabiker on 2007-06-30
Look at these cards/drivers.
[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html](http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11ag.html)

Get a driver that says "Monitor: Yes"

---

### Post by georgiabiker on 2007-06-30
(And by driver I actually meant to say "card". My bad)

---

### Post by nooor7772000 on 2007-07-01
ohh thanks alot so so much,,,,,,from my heart

---

### Post by motin on 2007-07-13
> **nooor7772000 said:**
> hi

when i open my terminal and use commands it say:-



Interface       Chipset         Driver

1.2.0kmprq
Monitor mode not supported, please upgrade


what that mean and how fix it please??
thanks

Why on EARTH didn't you write what commands you used? How are others supposed to give you support without knowing what you are doing?

A better approach would be:

> **nooor7772000 said:**
> hi

when i open my terminal and write "airmon-ng" it says:-



Interface       Chipset         Driver

1.2.0kmprq
Monitor mode not supported, please upgrade


what that mean and how fix it please??
thanks

---

