---
title: "Ethernet not working on Ubuntu 14.04"
date: 2015-01-27
forum: General Help
---

### Post by mohammed11 on 2015-01-27
Hi,

I have installed Ubuntu 14.04 using PXE build on a Lenovo L540 laptop.

There are 2 issues I have noticed.

If I boot to Windows 7, it shows a purple screen and doesn't do anything, so I would have to turn off the laptop to resolve that.

The major issue is that Ethernet is not working.  When I boot to Ubuntu, it says "Waiting for network configuration" and then waiting 60 seconds for it.  Yet there is no network connection.  I try to login with my domain account, it says invalid password.  But localadmin works.

I've noticed when it works, if the network cable is disconnected from the laptop, it stops working.

Does anyone know why this is happening?

---

### Post by ajgreeny on 2015-01-27
> **mohammed11 said:**
> Hi,

I have installed Ubuntu 14.04 using PXE build on a Lenovo L540 laptop.

There are 2 issues I have noticed.

If I boot to Windows 7, it shows a purple screen and doesn't do anything, so I would have to turn off the laptop to resolve that.

The major issue is that Ethernet is not working.  When I boot to Ubuntu, it says "Waiting for network configuration" and then waiting 60 seconds for it.  Yet there is no network connection.  I try to login with my domain account, it says invalid password.  But localadmin works.

[COLOR=#ff0000]I've noticed when it works, if the network cable is disconnected from the laptop, it stops working.[/COLOR]

Does anyone know why this is happening?
I don't understand what you mean by the comment I've highlighted in red; if you disconnect the network cable of course it stops working.

Can you confirm that you are talking of cable connection, not wireless, and can you also show the output of ```
lspci -nnk | grep -iA2 net
```which will show us your hardware.
Let's also see the content of your **/etc/network/interfaces** file.

---

### Post by mohammed11 on 2015-01-27
Sorry that red bit is true.  I meant to continue saying if I reconnect the cable, it still does not pick up the network connection.

This is the output for [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk | grep -iA2 net:[/FONT][/COLOR]00:19.0 Ethernet controller [0200]: Intel Corporation Ethernet Connection I217-LM [8086:153a] (rev 05)
	Subsystem: Lenovo Device [17aa:501e]
	Kernel driver in use: e1000e


And this is the content for the [COLOR=#000000] [/COLOR]**/etc/network/interfaces file:**
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet dhcp
# This is an autoconfigured IPv6 interface
#iface eth0 inet6 auto

---

