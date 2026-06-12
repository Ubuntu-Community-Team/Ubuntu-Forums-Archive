---
title: "network manager problem"
date: 2013-06-20
forum: General Help
---

### Post by nerdtron on 2013-06-20
How do I fix this?

[ATTACH=CONFIG]243972[/ATTACH]

My computer is connected via DHCP. But when I need to do a side project which required me to add a virtual interface eth0:0 and ip address to my system I edited the /etc/network/interfaces file.
```

auto eth0
iface eth0 inet dhcp


#iface eth0:0 inet static
#       address 10.1.0.10
#       netmask 255.255.255.0
#       network 10.1.0.0 

```

After my project, I commented the settings i have added. But now i noticed that the network icon on my taskbar is broken. It shows connection not managed. Still, though my network connection is fine. ifconfig shows I have obtained an IP address from the network.

---

### Post by steeldriver on 2013-06-20
If you want network manager to take back full control, you'll need to comment out the 'auto eth0 \ iface eth0 inet static' part as well (leaving just the 'lo' loopback definition) - network manager has its own config files and by default it ignores (considers 'unmanaged') any interfaces in /etc/network/interfaces. You can force n-m to 'manage' the ifupdown interfaces, using a setting in /etc/NetworkManager/NetworkManager.conf but it isn't recommended in most situations.

---

### Post by nerdtron on 2013-06-20
All right. I'll give it a try.


--UPDATE--

Thanks a lot. Then I just rebooted and enable/disable networking on the GUI network manager and its back to normal now.

---

