---
title: "static ip setup problem?"
date: 2013-08-24
forum: General Help
---

### Post by shamsat on 2013-08-24
The ubuntu 13.04 box is connected  to the ADSL router, the netwrok manager is enable and the router dhcp assign ip address to the eth0 in every boot, i want to confgire the eth0 for the static ip, i desable the network manager and confgiure the /etc/network/interface:
> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
allow-hotplug eth0
iface eth0 inet static
	address 192.168.1.10
        gateway 192.168.1.1
	netmask 255.255.255.0
	network 192.168.1.0
	broadcast 192.168.1.255
	# dns-* options are implemented by the resolvconf package, if installed
	dns-nameservers 192.168.1.1
        dns-search Router


But after boot there is no any network interface up and no any network connection avaliable:
> 
#ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:541 errors:0 dropped:0 overruns:0 frame:0
          TX packets:541 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:119261 (119.2 KB)  TX bytes:119261 (119.2 KB)


---

### Post by GwL3eNC on 2013-08-24
Hello,

i think you forgot the 

auto eth0

Else you must start the interface manualy. Insert auto eth0  over the

iface eth0 inet static

line.

---

### Post by nerdtron on 2013-08-24
First off, you must use the network manager GUI (if you have a GUI) to configure a static address. This program is different from the /etc/network/interfaces file and only one should manage your network settings.
If you really want to use the /etc/network/interfaces files, you can of course I think you forgot the

```
auto eth0
iface eth0 inet static
```

and then 
```
sudo ifdown eth0
sudo ifup eth0
```

Also, why does the eth0 doesn't show?
Try deleting the 70-persistent-net.rules files because it causes conflict when you change IP from DHCP to STATIC.
```
sudo rm /etc/udev/rules.d/70-persistent-net.rules 
```

Reboot and your problem should be fixed.

---

