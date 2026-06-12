---
title: "Booting taking about 10 minutes"
date: 2018-05-15
forum: General Help
---

### Post by dods100 on 2018-05-15
Hello!
I recently installed the ubuntu minimal (version 16.04) on a virtual machine and it was working completely fine. But i want this machine to run on an internal network, without any connection to my physical machine (testing virtual routers) but when i change my network adapter from NAT to internal network, my virtual machine takes roughly 10 minutes to start, stuck on the booting screen, and if i turn back to NAT, it boots instantly. I wonder if this is ubuntu trying to automatically download something with a huge timeout, or something like that. Any ideas on what should i do?
Thanks in advance

---

### Post by cruzer001 on 2018-05-15
Hello

Let it go through the 10 minute boot and then run:
```
systemd-analyze blame
```
This will display the boot process and time each process take to boot.

Guessing without seeing the output of that command, its network manager.

[https://www.google.com/search?client=ubuntu&hs=2Q1&channel=fs&ei=pxv7WtfqOYy4jwOlpb7IBA&q=systemd+analyze+blame+networkmanager&oq=systemd+analyze+blame&gs_l=psy-ab.1.0.0i71k1l8.0.0.0.105172.0.0.0.0.0.0.0.0..0.0....0...1..64.psy-ab..0.0.0....0._bM7LxiewzM](https://www.google.com/search?client=ubuntu&hs=2Q1&channel=fs&ei=pxv7WtfqOYy4jwOlpb7IBA&q=systemd+analyze+blame+networkmanager&oq=systemd+analyze+blame&gs_l=psy-ab.1.0.0i71k1l8.0.0.0.105172.0.0.0.0.0.0.0.0..0.0....0...1..64.psy-ab..0.0.0....0._bM7LxiewzM)

---

### Post by SeijiSensei on 2018-05-15
> **dods100 said:**
> when i change my network adapter from NAT to internal network

What do you mean by "internal network?" One that exists entirely in the virtual space?  If so, do you have a machine providing DHCP services in that network?  If not, did you set up static addressing and specify the machine's IP address and routing information manually?

If by "internal network" you mean a virtual machine that uses a bridged adapter, that should get its address as quickly as the host machine does.

---

