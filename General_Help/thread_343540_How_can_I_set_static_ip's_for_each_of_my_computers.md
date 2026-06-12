---
title: "How can I set static ip's for each of my computers?"
date: 2007-01-21
forum: General Help
---

### Post by thenetduck on 2007-01-21
hi, 
  I wanted to set static IP's for each of my computers. I just don't really know how to do that. Does anyone know? 

 The Net Duck

---

### Post by Shatrat on 2007-01-21
I prefer to do it through the router.
I assume you have a little Netgear or Dlink or some such other router?
If so you can log into it using 192.168.0.1 or 192.168.123.254 or whatever the local IP of your router is (check your router's website or manual) and set static DHCP IP assignments by mac address.
Sounds complicated but it isnt that hard if you poke around in your router.

---

### Post by dcstar on 2007-01-21
> **thenetduck said:**
> hi, 
  I wanted to set static IP's for each of my computers. I just don't really know how to do that. Does anyone know? 

 The Net Duck

In Ubuntu: System-Administration-Networking (or is it Networks?)

In Windows, Control Panel-Networking-Properties-TCP/IP for each network device.

---

### Post by reclusivemonkey on 2007-01-22
> **thenetduck said:**
> hi, 
  I wanted to set static IP's for each of my computers. 

Internal or External IPs?

---

### Post by PetePete on 2007-01-22
edit your /etc/network/interfaces file

comment out teh dhcp section... heres mine

```

# The primary network interface
auto eth0
#iface eth0 inet dhcp
iface eth0 inet static
address 192.168.2.11
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1

```

---

### Post by thenetduck on 2007-01-22
Thanks I got er done :)

---

