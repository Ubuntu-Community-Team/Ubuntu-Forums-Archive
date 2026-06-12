---
title: "HAL (hardware abstraction layer) cannot initialise"
date: 2007-01-13
forum: General Help
---

### Post by mattmole on 2007-01-13
Hi,

A couple of weeks back I installed Ubuntu 6.06.1 on my girlfriends, father's PC. Everything worked fine, I spent quite a time getting the wireless internet to work using  ndiswrapper, printer work, I have a virtual machine of XP installed to access the scanners, as xsane does not support them.

Everything worked nicely until a few days ago. When logging in an error box pops up stating "HAL cannot initialise".

There is nothing in /var/log/syslog about the HAL error, so dont know which way to turn! I also dont see any problems in dmesg relating to this.

The major problem I have at the moment is that I cannot load the virtual machine. Weird!

Thanks for you help. I will post any output of commands etc.

Cheers, Matt

---

### Post by dcstar on 2007-01-13
> **mattmole said:**
> Hi,

A couple of weeks back I installed Ubuntu 6.06.1 on my girlfriends, father's PC. Everything worked fine, I spent quite a time getting the wireless internet to work using  ndiswrapper, printer work, I have a virtual machine of XP installed to access the scanners, as xsane does not support them.

Everything worked nicely until a few days ago. When logging in an error box pops up stating "HAL cannot initialise".

There is nothing in /var/log/syslog about the HAL error, so dont know which way to turn! I also dont see any problems in dmesg relating to this.

The major problem I have at the moment is that I cannot load the virtual machine. Weird!

Thanks for you help. I will post any output of commands etc.

Cheers, Matt

Sometimes an update can break things like this, other times a power shutdown (not just a reboot) resolves it.

---

### Post by mattmole on 2007-01-14
Thanks for that. On next bootup the problem had gone away. I will post again if it happens often!

Any idea what causes it?

Thanks, Matt

---

