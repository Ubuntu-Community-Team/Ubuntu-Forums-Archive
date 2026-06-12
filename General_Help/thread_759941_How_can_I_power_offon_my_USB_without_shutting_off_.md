---
title: "How can I power off/on my USB without shutting off machine?"
date: 2008-04-19
forum: General Help
---

### Post by unutbu on 2008-04-19
Occassionally my wireless connection stops and I have not found a way to regain a connection except by rebooting the machine. I find I must shutdown and power on -- a soft reboot does not work.

I've tried both DHCP and Static connections, but the problem persists.

ifconfig looks fine; iwconfig shows the access point and essid, and iwlist scanning shows the D-Link WUA-2340 Wireless G USB adapter detects the router too. The routing table also looks fine before and after the connection stops.

This problem is a little hard to debug because it only happens occassionally and I don't know how to recreate the problem on demand.

So, I'm wondering if there is a way to simulate a power off/power on without having to turn off my machine. I think it is only the USB network adapter that needs to be powered off/on. Disconnecting the adapter and reconnecting it did not work.

---

### Post by ibuclaw on 2008-04-19
I would say that the commands```
rmmod **<device>**
```
Followed by```
modprobe **<device>**
```
Would be the best way to do a restart of the device, but since you say that it is a USB device, am I right in assuming that you use ndiswrapper?

If so, the first command may crash your system, as in freeze indefinately until you give up and hard-reboot. (ndiswrapper can't handle being unloaded from the kernel while it is active for some bizarre reason).

Regards
Iain

---

### Post by unutbu on 2008-04-19
Yep, 

```
sudo rmmod ndiswrapper
```

freezes the machine. (Thanks for the warning; I tried it anyway).

---

