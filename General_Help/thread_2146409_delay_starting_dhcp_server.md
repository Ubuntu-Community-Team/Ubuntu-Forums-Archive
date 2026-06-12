---
title: "delay starting dhcp server"
date: 2013-05-18
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-05-18
Sorry if the belong in the networking & wireless sub-forum.
i found this, it seems close to what i want to do
[http://askubuntu.com/questions/3651/how-can-i-start-dhcp3-server-later-so-that-it-waits-for-a-bridge-interface-to-i](http://askubuntu.com/questions/3651/how-can-i-start-dhcp3-server-later-so-that-it-waits-for-a-bridge-interface-to-i)
this is currently in my [FONT=courier new]/etc/network/interfaces[/FONT] file
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```
during the boot process [FONT=courier new] isc-dhcp-server[/FONT] tries to startup several times and fails 
this is in my [FONT=courier new]/etc/rc.local[/FONT] script cause i don't know the proper way to do this
```
echo 1 > /proc/sys/net/ipv4/ip_forward
while [ 0`pidof NetworkManager` -eq 0 ]; do # wait for net manager to start so ifconfig will work right
    sleep 1
done
while [ "`ifconfig eth0 | grep 'inet addr:'`" = "" ]; do # wait for external IP address
    sleep 2
done
while [ "`ifconfig eth0:1 | grep 'inet addr:'`" = "" ]; do # create new net interface
    sleep 2
    ifconfig eth0:1 10.0.0.1 netmask 255.255.0.0
done
# make new interface do what is needs to do
#iptables -t nat -A PREROUTING -o eth0 -p tcp -m tcp --dport 80 -j DNAT --to-destination 10.0.0.75:80
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables -P FORWARD ACCEPT
service isc-dhcp-server start
```
how should i do this, should i just add this to my [FONT=courier new]/etc/network/interfaces[/FONT] file
```
iface eth0:0 inet static
    bridge_ports eth0 eth0:1
    address 10.0.0.1
    broadcast 10.0.0.255
    netmask 255.255.0.0
    post-up /etc/init.d/isc-dhcp-server start
    pre-down /etc/init.d/isc-dhcp-server stop
```
if that will work what do i do to my [FONT=Courier New]/etc/rc.local[/FONT] script

---

