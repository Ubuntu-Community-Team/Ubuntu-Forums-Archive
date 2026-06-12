---
title: "Networking Problem"
date: 2007-04-12
forum: General Help
---

### Post by Fuqaha on 2007-04-12
Hi,

I am a TOTAL n00b in Ubuntu / Linux. Ive just installed 7.04 FF A5 Ubuntu. All went fine but i have trouble configuring the networking.

In window environment, my network config is like this
ip : 192.168.105.40
subnet : 255.255.255.0
gateway : 10.10.0.4
dns : 192.168.10.1 , 192.168.10.2

ive manage to configure thru Network and insert ip,subnet and gateway and dns on the other tab.

But the network icon at the top right corner of the desktop shows "No network device found".

But I can browse the local networks tho'.

What went wrong?

my PC specs
Intel DG965RY motherboard
Core 2 Duo 6400 2.13Ghz
250Gb Western Digital HDD
2Gb 667 Kingston DDR2 RAM
Samsung SyncMaster 940bw 19" Wide screen monitor
ATi Radeon x1300 Pro graphic card 1440 x 900

**I am sorry for posting this, im really a n00b and already tried googling, but to no avail.**

Ive tried 6.10 version, but there seems to be an issue with the display.

Thanks.

=)

---

### Post by rmemm on 2007-04-12
I'm assuming you can see your local net but not the internet?

What looks strange about your setup to me is your gateway address.  Generally for your network mask you need a gateway address thats 192.168.105.x where x is a number from 1 to 254 and is the IP address of the router for your local network.  Often the gateway is 192.168.105.1. If the 10.x.x.x address is correct then your local net is a bit strange in my mind.

Other thing you could try is just turn on DHCP -- that's how most workstations are provisioned today anyway -- this of course depends on your local network setup.

Rob

---

### Post by rmemm on 2007-04-12
Another comment--if your not familar with network masks--what they mean is that for all fields that are 255 -- then if theres and IP number difference between the IP your connecting to and your workstation IP -- then route this data through the gateway you specify.  Otherwise assume (for differences only in the 0 fields of the mask) that the IP your referencing is on the local network and does not need to be routed.

Generally what this means is that the gateway has to be an IP address on your local network -- meaning the fields in the gateway address that correspond to 255 parts of the network mask normally match your workstations IP address in those parts and only the 0 fields are different.

Maybe there are other configurations used -- but I've not seen them.

Rob

---

### Post by alex_anthony on 2007-04-13
I would advise Edgy. In my experience, display issues are easier than networking.
If your display issue is a distortion, 915resolution might fix it.
Edgy is also stable

---

### Post by zvacet on 2007-04-13
system>administration>highlight your modem>properties>dhcp>chek upper left box>close
In DNS tab replace address you find there with your nameservers>close
```
pppoeconf
```

---

