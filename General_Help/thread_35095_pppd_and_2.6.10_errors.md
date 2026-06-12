---
title: "pppd and 2.6.10 errors?"
date: 2005-05-17
forum: General Help
---

### Post by Rycuda on 2005-05-17
Using Hoary wvdial (version 1.54.0) and pppd (version 2.4.2). Hardware is an external serial modem over a standard 56.6kbps dialup connection.

On upgrading to kernel 2.6.10 using wvdial, the standard chatter goes back and forth till pppd is started then, from the syslogs it dies with the following error output:

ioctl(SIOCADDRT) device route: Network is down (line 2479)

Same error on every connect. Tried using a different set of dialup details, in the end reverted to 2.6.9.

---

### Post by wwwolf on 2005-05-17
[QUOTE=Rycuda]Using Hoary wvdial (version 1.54.0) and pppd (version 2.4.2). Hardware is an external serial modem over a standard 56.6kbps dialup connection.

On upgrading to kernel 2.6.10 using wvdial, the standard chatter goes back and forth till pppd is started then, from the syslogs it dies with the following error output:

ioctl(SIOCADDRT) device route: Network is down (line 2479)

Same error on every connect. Tried using a different set of dialup details, in the end reverted to 2.6.9.[/QUOTE]

I'm using 2.6.10-5-386 and it works fine for me. Did you compile the kernel yourself?

HTH,

---

### Post by Rycuda on 2005-05-18
It is a self compiled kernel. However it is running on the same configuration as the working 2.6.9. Self compiled to reduce modules loaded for drivers, and to include iprouting modules, and bridging support.

---

