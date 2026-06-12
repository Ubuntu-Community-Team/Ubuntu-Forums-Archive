---
title: "What does this mean?"
date: 2008-03-10
forum: General Help
---

### Post by gilloz on 2008-03-10
Everytime I start my computer and I look at the System Log, there is a WARNING message embedded several times in the boot sequence which says, "dhcdbd is not running"  What is that and how do I get it to run, or should I even care?

---

### Post by ibuclaw on 2008-03-10
DHCDBD - 
> dhcdbd provides a D-BUS interface to the ISC dhclient software. The daemon provides access to DHCP configuration operations and stores those options persistently. Other D-BUS applications can receive notifications of changes in the client's DHCP configuration.

DHCLIENT - 
> The DHCP protocol allows a host to contact a central server which maintains a list of IP addresses which may be assigned on one or more subnets

Does that sound relevant to your system to you? Are you on a server/network?

To be honest, 9 times out of 10 the boot up script loads up a list of processes that will allow almost any hardware setup to run out of the box. And as every PC isn't the same, modules fail to run because you don't have the hardware for it to run. This is not a bad thing, I've had a computer with no soundcard once and an a big red [COLOR="Red"][FAILED][/COLOR]  would show when the boot up manager started to load the ALSA sound config.
And in my case, I wouldn't want ALSA to load anyway! With nothing for it to control, it'll just waste precious memory space.

You can change the bootup script and have it removed, though it's requires opening config files, and is really not necessary.
Overall, no problem. Nothing to worry about.

Iain

---

### Post by por100pre1 on 2008-03-10
> **gilloz said:**
> Everytime I start my computer and I look at the System Log, there is a WARNING message embedded several times in the boot sequence which says, "dhcdbd is not running"  What is that and how do I get it to run, or should I even care?

Install BootUp-Manager,

```
sudo apt-get install bum
```

start it,

```
gksu bum
```

and then look for **D-Bus interface to the ISC DHCP client**. Be sure it is checked and then click **Apply**. Then restart your system.

```
sudo reboot
```

That service can be useful with routers or networks.

Hope it helps. :)

---

### Post by gilloz on 2008-03-11
Thanks Tinivole and por100pre1for your responses.  Out of curiosity, I ran por100pre1's procedure and indeed D-Bus Interface was already checked.  Thanks again.

---

