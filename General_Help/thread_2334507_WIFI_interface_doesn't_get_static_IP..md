---
title: "WIFI interface doesn't get static IP."
date: 2016-08-20
forum: General Help
---

### Post by tajiknomi on 2016-08-20
I am trying to assign static ip to my PC. I have configured the /etc/network/interfaces as bellow

> auto lo
iface lo inet loopback


iface wlo1 inet static
address 192.168.1.20      // Want to assign this IP
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 192.168.1.1

"wlo1" is the logical name of my wifi interface (via lshw)

I have configure my /NetworkManager.conf as follows

> [main]plugins=ifupdown,keyfile,ofono
# dns=dnsmasq


[ifupdown]
managed=true


Still my ifconfig shows me that i'm getting 192.168.1.2 from my router.

I don't know what i am missing !!

Any help would be appreciated. thanks

---

### Post by gordintoronto on 2016-08-20
What version of Linux?

I find it's easier to get a static address by configuring the router to assign the address based on the HWaddr provided by ifconfig.

---

### Post by steeldriver on 2016-08-20
^^^ agree with that (it's usually referred to as 'address reservation')

However, if you still want to set a true static, then since you are using network-manager you should allow THAT rather than the /etc/network/interfaces file - edit the connection and under 'IPv4 Settings', chose 'Manual' and fill in the boxes accordingly

---

### Post by Bucky Ball on 2016-08-20
Just go to the network manager icon, click and Edit Connections, choose you connect and set the static IP there. Set a range on the router for it to serve IPs through DHCP if you need it to and set your static outside that range. Done.

Don't bother with /etc/network/interfaces. It and Network Manager don't play and what goes in there won't necessarily register with Network Manager. If you are using Network Manager that will take precedence.

* For instance, set the DHCP on the router to serve IPs between 192.168.0.100-110 and set your static *on the machine, not the router*, to 192.168.0.111. 

I've never set up static IPs any other way and that's all I use. Never touched the /etc/network/interfaces file for this.

---

