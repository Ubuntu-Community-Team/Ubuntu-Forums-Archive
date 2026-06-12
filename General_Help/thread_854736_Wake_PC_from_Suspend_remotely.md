---
title: "Wake PC from Suspend remotely?"
date: 2008-07-09
forum: General Help
---

### Post by KenBW2 on 2008-07-09
It's probably impossible, but is there a way to wake a PC from Suspend remotely across my LAN using ssh or somesuch?

---

### Post by ModelM on 2008-07-09
I've never used it & so know nothing about it, but I think you're looking for Wake on Lan (WOL) capability. Some network cards have it, some don't. Some motherboards can do it, some can't.

---

### Post by KenBW2 on 2008-07-09
Thanks ModelM.
I found a package called etherwake, which I've installed and attempted to figure out. When I try to use it it get
```

kenneth@kenneth-laptop:~$ sudo etherwake -b 192.168.11.130
[sudo] password for kenneth:
etherwake: The Magic Packet host address must be specified as
  - a station address, 00:11:22:33:44:55, or
  - a hostname with a known 'ethers' entry.

```

my PC's hostname is kenneth-desktop if that helps.
Could anyone help m with this?
Thanks

---

### Post by sdennie on 2008-07-09
You can probably do this.  It's a function of setting your motherboard to do it and using something like:

```

sudo ethtool -s eth0 wol p

```

And possibly sending some values to /proc/acpi/wakeup (which defines what methods the machine can wakeup with).  You may also need to setup pm-utils to reset the WOL values after it wakes up.  There is some good discussion of the issue here: [http://ubuntuforums.org/showthread.php?t=814939](http://ubuntuforums.org/showthread.php?t=814939)

---

### Post by ModelM on 2008-07-09
> **KenBW2 said:**
> Thanks ModelM.
I found a package called etherwake, which I've installed and attempted to figure out. When I try to use it it get
```

kenneth@kenneth-laptop:~$ sudo etherwake -b 192.168.11.130
[sudo] password for kenneth:
etherwake: The Magic Packet host address must be specified as
  - a station address, 00:11:22:33:44:55, or
  - a hostname with a known 'ethers' entry.

```

my PC's hostname is kenneth-desktop if that helps.
Could anyone help m with this?
Thanks

etherqwake is asking for the MAC address, not the IP address. Substitute the MAC address in the command line you used & I'm guessing it will work.

---

