---
title: "Openvpn help: not forwarding browser traffic"
date: 2008-05-16
forum: General Help
---

### Post by headlice on 2008-05-16
Hi,

Ok, I have openvpn server running on Ubuntu Hardy server that sits behind dd-wrt router with openvpn enabled on it as well.

I am using Nokia n800 client.

I can connect to server just fine, but I cannot forward browser traffic.

Dont know if this is the reason, but this is what the server sends to the client:

```
PUSH: Received control message: 'PUSH_REPLY,route 192.168.1.0 255.255.255.0,redirect-gateway,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig 10.8.0.6 10.8.0.5
```

This is the client's response:

```
Options error: Unrecognized option or missing parameter(s) in [PUSH-OPTIONS]:4: topology (2.0.7)
```

could someone help with this?  Also, is this the reason why I am not being able to forward browser traffic?

---

### Post by headlice on 2008-05-16
Ok, I just received another message from the client terminal:
```

TCP/UDP: Incoming packet rejected from 127.0.0.1:53[2], expected peer address: *myipaddress:port#* (allow this incoming source address/port by removing --remote or adding --float)
```

---

### Post by SpaceTeddy on 2008-05-16
can you please post the config of the client and the server. Also, have you enabled masquerading on the server of all outgoing traffic and have you enabled ip_forwarding ?

let's see if we can figure this out :)

---

### Post by headlice on 2008-05-16
Server config:
```
port (my specified port #)
proto udp
dev tun
ca /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/ca.crt
cert /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/Server1.crt
key /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/Server1.key  
dh /usr/share/doc/openvpn/examples/easy-rsa/2.0/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.0 255.255.255.0"
push "redirect-gateway"
keepalive 10 120
persist-key
persist-tun
status openvpn-status.log
verb 3
mute 20
```

Client config:
```
client
dev tun
proto udp
remote (my ipaddress# my port#)
resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
cert n800.crt
key n800.key
ns-cert-type server
verb 3
--explicit-exit-notify 2
```

Not sure if I have masquerading on or not...I believe I did enable IP forwarding using this command:

sudo nano /etc/sysctl.conf

uncommented net.ipv4.ip_forward = 1

saved, exited, and typed:

sysctl -p
sysctl -w net.ipv4.route.flush=1

ETA: I do not have any software firewall on my Ubuntu box.  Do I still need to set rules for iptables?

---

### Post by headlice on 2008-05-17
OMG I got it working!!!

Space Teddy, you were right- I wasnt masquerading.

looked more on the openvpn site, specifically here:

[http://openvpn.net/index.php/documentation/howto.html#redirect](http://openvpn.net/index.php/documentation/howto.html#redirect)

and realized that in the server.conf it needed to have 

```
push "redirect-gateway def1"
``` instead of ```
push "redirect-gateway"
```

Also, I needed code for iptables to masquerade through my eth0 card on my server.  This code did the trick:

```
sudo iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```

woohoo!

---

### Post by Gorkhaan on 2008-07-15
Hi Headlice!

I'm trying to get to work the MASQUERADING but it does not works. If I call

```
iptables -L
```
after I entered the masquerading command for my ubuntu, it shows nothing! :(

Can you help me out?

I'm curious about your iptables -L and your modules.

```
iptables -L
modprobe -l
```

You can copy the modprobe list to a textfile to post it back to me.

```
modprobe -l >> modules
gedit modules
```

I look forward to hearing from you ASAP,

thank you,

Gorkhaan



Okay, I solved my problem! I had to add a default gateway, and it works now.

---

