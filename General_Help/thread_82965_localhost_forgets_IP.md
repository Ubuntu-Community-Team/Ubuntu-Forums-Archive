---
title: "localhost forgets IP"
date: 2005-10-27
forum: General Help
---

### Post by MrMinute on 2005-10-27
Hello!

I use DHCP in my network. Everytime I run dhclient to get an IP address my localhost forgets it's IP address. I have to run "ifconfig lo 127.0.0.1" afterwards to fix it. Also when using the menu system->administration->network and add a new DNS server, it is not stored but forgotten in the next moment.

A minor important thing which disturbs me is why I have to run dhclient manually when switching to another LAN which is using DHCP? It would be more comfortable if Ubuntu recognizes the new connected network cable and fetchs an IP address automatically.

Thanks for your help!

---

### Post by mykey on 2005-10-27
make your network static and those probs are history - just assign a static IP once and thats it

---

### Post by MrMinute on 2005-10-28
To use a static network configuration is not so useful for me because I use the computer (laptop) in different networks. Does it mean DHCP is not working with Ubuntu properly by default?

---

### Post by dhpeterson on 2005-10-28
[QUOTE=MrMinute]Hello!

I use DHCP in my network. Everytime I run dhclient to get an IP address my localhost forgets it's IP address. I have to run "ifconfig lo 127.0.0.1" afterwards to fix it. Also when using the menu system->administration->network and add a new DNS server, it is not stored but forgotten in the next moment.

A minor important thing which disturbs me is why I have to run dhclient manually when switching to another LAN which is using DHCP? It would be more comfortable if Ubuntu recognizes the new connected network cable and fetchs an IP address automatically.

Thanks for your help![/QUOTE]


Have you tried running dhclient on the specific interface you're trying to configure, e.g. 

# dhclient eth0

If this works okay you might want to edit your /etc/network/interfaces file to make this permanent and then do a /etc/init.d/networking restart (or simply reboot). Here's my interfaces file:

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


HTH

Dave

---

### Post by MrMinute on 2005-10-28
[QUOTE=dhpeterson]Have you tried running dhclient on the specific interface you're trying to configure, e.g. 

# dhclient eth0
[/QUOTE]

This works fine!

[QUOTE=dhpeterson]If this works okay you might want to edit your /etc/network/interfaces file to make this permanent and then do a /etc/init.d/networking restart (or simply reboot). Here's my interfaces file:

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
[/QUOTE]

My file looks the same but it has an additionally "auto eth0" at the end.

So how to get Ubuntu to call "dhclient eth0" each time a network cable is plugged in and how to define an additional nameserver (manually) while using DHCP?

---

### Post by MrMinute on 2005-10-30
To define a DNS while using DHCP can be done by editing the file

```
sudo editor /etc/dhcp3/dhclient.conf
```

and add a line like

```
prepend domain-name-servers 111.222.333.444
```

where 111.222.333.444 is the IP of the DNS. That's it.

I did not(!) figured out how to execute "dhclient eth0" automatically when a cable is pluged into eth0. Any suggestions are welcome!

---

