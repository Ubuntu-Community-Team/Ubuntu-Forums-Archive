---
title: "kvm/qemu configure dhcp/specify different IP address"
date: 2008-06-10
forum: General Help
---

### Post by ema on 2008-06-10
Hi all,

I'm successfully using kvm (Ubuntu 8.04), running WindowsXP SP2 virtual OS.
I can browse the web, and should not have any issue with TCP/IP and UDP/IP software.

The problem is that I have a default address of the class 10.*.*.*
I need to use the virtualized XP to run a remote desktop software inside it and I fear that the 10.*.*.* class is present in a remote network I'm trying to connect on (so the packets destined to the 'real' 10.*.*.* hosts get lost under the virtual dhcp).

Is there a way (simple maybe) to configure the DHCP kvm/qemu addresses at command line, without having to install/configure any other complex software?

I'd like to use maybe another class of addresses like
192.168.1.* or 192.168.254.* or whatever, just different from 10.*.*.*

Thanks in advance,
Ema.

---

### Post by ema on 2008-06-10
Should this be moved to a more appropriate scetion?
Which one do you suggest to move it?

Cheers,

---

