---
title: "Startup service fail"
date: 2013-04-08
forum: General Help
---

### Post by babisayabundar on 2013-04-08
My ubuntu 12.04 failed to start some service.
when ubuntu's booting it says "waiting for network service to configure", then it says again "waiting 60 seconds more to configure network". After waiting so long, it says "booting without full network support".

Can anyone tell me what's happened?

---

### Post by slickymaster on 2013-04-08
After you see "Booting system without full network configuration" press Ctrl+Alt+F1 to get you to the shell prompt. Use a shell text editor like nano to change [B]/etc/network/interfaces
[/B]I think the default contents of the interfaces file in 12.04 was something like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by CharlesA on 2013-04-08
I've seen that message when the machine is unable to get an IP address from DHCP. Causes could be the DHCP server could be having problems or the network cable came unplugged.

---

