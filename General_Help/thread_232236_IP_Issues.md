---
title: "IP Issues"
date: 2006-08-08
forum: General Help
---

### Post by Mickey1 on 2006-08-08
Under windows i seem to have a static ip
But under linux it seems to become dynamic 

Is there a way to fix this

I receive my ip through dhcp under windows 

Dunno if it does under ubuntu

This causes some issues with my eggdrop that i have running and would like to see this fixed

Any help would be appreciated

---

### Post by steve.horsley on 2006-08-08
Can you post the output from the command > cat /etc/network/interfaces


Or you could look in System->Administration->Networking and see what's configured

---

### Post by Ocxic on 2006-08-08
simply set the dhcp server on the windows box to provide u with a static ip, I'm sure there an option, somwhere being in widows. u won't have to change a thing on you comp

---

### Post by Mickey1 on 2006-08-13
cheers m8s
will give this a go :)

---

### Post by Mickey1 on 2006-08-13
> **Ocxic said:**
> simply set the dhcp server on the windows box to provide u with a static ip, I'm sure there an option, somwhere being in widows. u won't have to change a thing on you comp

I have a static ip on windows

It just keeps changing everytime i boot up on linux

---

### Post by brundles on 2006-08-13
I think what you're seeing on the Windows side is Microsoft's approach of trying to be helpful while not following the rules. XP has a habit of assuming it will get the IP it had last time (assuming the lease hasn't expired) and configuring itself so - causing pain in a LAN until the DHCP server corrects it. AFAIK it can request the same IP but shouldn't use it until it's told so.

How often do you boot to Ubuntu? If you do two consecutive Ubuntu restarts, do you get the same IP address both times then?

I'm wondering if the problem is tied in to how long between reboots and the lease expiry time.

One way around this - would be to use a router between your internet connection and the PC. The router will then remember the MAC address of the card in the PC and re-assign the same local IP while at the same time always keeping the same external IP on the router.

---

### Post by Mickey1 on 2006-08-14
> **steve.horsley said:**
> Can you post the output from the command 

Or you could look in System->Administration->Networking and see what's configured
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
auto eth0

# The primary network interface
iface eth0 inet dhcp

```

cheers in advance

---

### Post by Mickey1 on 2006-09-02
nothing on this then? :(

---

