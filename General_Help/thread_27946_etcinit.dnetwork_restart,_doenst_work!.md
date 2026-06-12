---
title: "/etc/init.d/network restart, doenst work!"
date: 2005-04-18
forum: General Help
---

### Post by wetenschapper on 2005-04-18
hey,

when modify my /etc/network/interfaces (set a static IP-address)
and then restart the network services, my ip-address isn't changed

*sudo vi /etc/network/interfaces*

**the /etc/network/interfaces:**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface
iface eth0 inet dhcp
#iface eth0 inet static
#address 10.222.111.7
#netmask 255.0.0.0
#broadcast 192.168.0.255

btw: what is the hotplug for? when I outcomment it, my dhcp doens't work

I restart this way:
jan@laxtop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ ok ]

and then check with: [U]sudo ifconfig eth0
[/U]and the ip address is still the same

what am I doing wrong?

---

### Post by heimo on 2005-04-18
Erhm... Maybe I misunderstood you, but are you trying to change the IP to static? You need to have those lines uncommented. 

```
 # iface eth0 inet dhcp 
iface eth0 inet static
address 10.222.111.7
netmask 255.0.0.0
broadcast 192.168.0.255

``` 
 
hotplug (as far as I know) can bring up or down your interfaces according to the status of connection (cable attached / not attached)
 
Did this help?

---

### Post by wetenschapper on 2005-04-18
I know I have to uncomment it, and the broadcast is not right, the config should be right, 

when I reboot with the modifyed config it works, but this should work when I restart the services right? it did under Gentoo....

the hotplug is strange, because when i boot with hotplug uncommented and dhcp on it doens't work, when i boot with dhcp on and hotplug it does, 

this is so strange

---

### Post by heimo on 2005-04-18
Yup. */etc/init.d/networking restart* should reload it, but you can as well just do *ifdown eth0 *and [i]ifup eth0

[/i]Bring down the interface, change config, bring it up and check with *ifconfig eth0 - *if it doesn't have the new configuration, it's probably reading it from some other place (unlikely).

---

