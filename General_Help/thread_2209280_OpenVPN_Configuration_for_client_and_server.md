---
title: "OpenVPN Configuration for client and server"
date: 2014-03-04
forum: General Help
---

### Post by amish_otaku on 2014-03-04
Ok, so I've been banging my head on this matter trying to get an openVPN server/client up and running. I've managed to get the server part of it setup, but it's not acting right. Basically what I am wanting to happen is to create an openVPN bridged setup. I would prefer that this automatically pushes a DHCP address across the VPN without having to deal with the DHCP on the openVPN server itself.

Server Info
Ubuntu 12.04 x64
UFW is disabled

server.conf
```

port 1194
proto tcp
dev tap0 
ca ca.crt
cert openvpn.crt
key openvpn.key  # This file should be kept secret
dh dh2048.pem
server-bridge 172.31.0.200 255.255.255.0 172.31.0.40 172.31.0.45
push "route 172.31.0.254 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
client-to-client
keepalive 10 120
tls-auth ta.key 0
cipher AES-128-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
mute 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3

```

The original guide that I followed was located at [www.slsmk.com/installing-openvpn-on-ubuntu-server-12-04-using-tap/]("http://www.slsmk.com/installing-openvpn-on-ubuntu-server-12-04-using-tap/")

I pretty much followed the guide to a "T". I've made changes to the network as applicable for my internal LAN. Can someone please help me figure this out?

I can't quite seem to make this work properly. Help???

---

### Post by amish_otaku on 2014-03-05
bump

---

### Post by nerdtron on 2014-03-06
(This thread should be move to the Server Platforms)

We need to debug your configuration to see what is happening.
Add this line to your server.conf
```
log-append /etc/openvpn/openvpn.log
```

And change your verbosity to 5
```
verb 5
```

Now restart the openvpn service.
Then we need to see the logs.
```
tailf -n 100 /etc/openvpn/openvpn.log
```

By doing this, you can have a live status on what is happening when a client tries to connect.
Now try connecting a client, you should see the logs scroll and post them here.

---

### Post by amish_otaku on 2014-03-07
I will try to accomplish that when I can get back to my computer at home this evening. I'm located at UTC time code -6 so I am not sure what time that is where you live, but I will update as I have more info.

---

### Post by amish_otaku on 2014-03-08
Ok... I've managed to get the client to connect using what you had specified I do so that I could see the logs, and managed to get it worked out as far as the connecting. I am curious though as to why the following line does not hand out an IP address in the range although this is not what I want it to do, it still doesn't act properly. 

```
server-bridge 172.31.0.200 255.255.255.0 172.31.0.40 172.31.0.45
```

Also I've found that if I try to specify the TLS in the configuration it refuses to connect. The only way I've managed to get it running is with out that line. Although I would like to have the extra security just to fix my paranoia. 

Lastly, I can't ping across the VPN or access and network shares. I've enabled the IPV4 Forwarding in sysctrl.conf and made sure that the UFW firewall is disabled. Only thing I can think is that it might be something to do with IPTables, but I am by no means an expert in this arena. I've posted all of my relevant configs below. Please any help would be appreciated.

Server IP configuration
```

# The loopback network interface
auto lo
iface lo inet loopback
auto br0
iface br0 inet static
address 172.31.0.200
netmask 255.255.255.0
gateway 172.31.0.254
network 172.31.0.0
broadcast 172.31.0.200
bridge_ports eth0
bridge_fd 9
bridge_hello 2
bridge_maxage 12
bridge_stp off
dns-nameservers 8.8.8.8 8.8.4.4

iface eth0 inet manual
up ifconfig $IFACE 0.0.0.0 up
up ip link set $IFACE promisc on
down ip link set $IFACE promisc off
down ifconfig $IFACE down

```

server.conf
```

#local a.b.c.d
port 1194
proto tcp
#proto udp
dev tap0
#dev tun
#dev-node MyTap
ca ca.crt
cert openvpn.crt
key openvpn.key
dh dh2048.pem
#server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
#server-bridge 10.8.0.4 255.255.255.0 10.8.0.50 10.8.0.100
server-bridge 172.31.0.200 255.255.255.0 172.31.0.40 172.31.0.45
#server-bridge
push "route 172.31.0.254 255.255.255.0"
#client-config-dir ccd
#route 192.168.40.128 255.255.255.248
#client-config-dir ccd
#route 10.9.0.0 255.255.255.252
#learn-address ./script
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
client-to-client
#duplicate-cn
keepalive 10 120
#tls-auth ta.key 0
cipher AES-128-CBC
comp-lzo
#max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 5
mute 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3
log-append /etc/openvpn/openvpn.log

```

client.ovpn
```

remote www.xxx.yyy.zzz
port 1194
proto tcp-client
tls-client
dev tap
ca "C:\\Program Files\\OpenVPN\\config\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\config\\client.crt"
key "C:\\Program Files\\OpenVPN\\config\\client.key"
dh dh2048.pem
keepalive 10 120
cipher AES-128-CBC
comp-lzo
persist-key
persist-tun
verb 5
mute 3
```

---

### Post by amish_otaku on 2014-03-17
Currently I can get connected, but cannot get what I want working. I want to route all traffic across the VPN and not just traffic on the same subnet. Basically I want the VPN WAN to become my WAN. I have tried with push routes, redirect-gateway and so on. No luck. Does anyone have any ideas?

server.conf
```
port 1194
proto tcp
dev tap0
ca ca.crt
cert openvpn.crt
key openvpn.key
dh dh2048.pem
server-bridge 
push "route 172.31.0.0 255.255.255.0 vpn_gateway"
push "dhcp-option DNS 172.31.0.254"
client-to-client
keepalive 10 120
cipher AES-128-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 5
mute 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3
log-append /etc/openvpn/openvpn.log

```

client.conf
```

remote [www.xxx.yyy.zzz]("http://www.xxx.yyy.zzz")
port 1194
proto tcp-client
dev tap
tls-client
ca "C:\\Program Files\\OpenVPN\\config\\ca.crt"
cert "C:\\Program Files\\OpenVPN\\config\\client.crt"
key "C:\\Program Files\\OpenVPN\\config\\client.key"
dh dh2048.pem
keepalive 10 120
cipher AES-128-CBC
comp-lzo
persist-key
persist-tun
route-gateway 172.31.0.254
route-method exe
route-delay 10
verb 5
mute 3

```

Is this possible with a bridged VPN or do I need to set a custom route on the client?

---

### Post by nerdtron on 2014-03-18
Once you client is connected, what is the output of
```
route -n
```

Try adding a default route manually on the client such as
```
sudo route add default gw [VPN IP address] 
```

---

### Post by Andreas_Hiebsch on 2014-03-18
Try to change the server.conf

port 1194
proto tcp
dev tap0
ca ca.crt
cert openvpn.crt
key openvpn.key
dh dh2048.pem

#----------------NIC IP------SUBNET-------DHCP FOR CLIENTS------
server-bridge 172.31.0.X 255.255.255.0 172.31.0.10 172.31.0.20     
push "route 172.31.0.0 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp" #IMPORTANT!!!

push "dhcp-option DNS 172.31.0.254"
client-to-client
keepalive 10 120
cipher AES-128-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 5
mute 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3
log-append /etc/openvpn/openvpn.log

Andreas

---

