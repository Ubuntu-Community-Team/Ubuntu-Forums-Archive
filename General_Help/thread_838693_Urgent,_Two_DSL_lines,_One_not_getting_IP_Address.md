---
title: "Urgent, Two DSL lines, One not getting IP Address"
date: 2008-06-23
forum: General Help
---

### Post by beckols on 2008-06-23
I have a server with 3 ethernet connections, 1 for the LAN and two for separate DSL lines.  I just now connected the second DSL line, but it isn't getting an IP Address.

/etc/network/interfaces
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0 eth1 eth2
iface eth0 inet static
        address 10.1.1.1
        netmask 255.255.255.0
        network 10.1.1.0
        broadcast 10.1.1.255
        gateway 10.1.1.1
iface eth1 inet dhcp
iface eth2 inet dhcp
```

eth1 is the one that isn't getting an IP address.

---

### Post by jimv on 2008-06-23
can you post the output of ifconfig?

---

### Post by beckols on 2008-06-23
Well you see, this giant piece of crap decided to die on me now... its an old Dell Dimension 4300, and the hard drive shows up in BIOS under Primary Hard Drive but not in the boot sequence.  And neither does the CD Drive.  I thought it might be a problem with the IDE channel, but I tried both of them, and besides it was still noticing it in the BIOS so idk.  I don't have a floppy drive in any of my machines here, so I'm going to wait until I get to work tomorrow and get a BIOS update and see if that does the trick.  So hopefully tomorrow I will be back to at least a semi-working server :( :(

---

### Post by jimv on 2008-06-24
That sucks.  Good luck!

---

### Post by beckols on 2009-05-19
This was a while ago, but I thought I would close the ticket.  Apparently, the ISP (or possibly it's the fault of the modem(s)) will not allow a machine to receive a new DHCP lease so quickly while the current lease is still good.  This seems moderately obvious now or else people would be taking out multiple leases all the time.  I just have to remember in the future to have room for bit of downtime if I'm going to switch hardware.

---

