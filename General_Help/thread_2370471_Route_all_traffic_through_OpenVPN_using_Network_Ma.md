---
title: "Route all traffic through OpenVPN using Network Manager?"
date: 2017-09-03
forum: General Help
---

### Post by Roasted on 2017-09-03
Hi friends. I'm on a mixture of Ubuntu Gnome 16.04/17.04 and my server is Ubuntu Server 16.04. I used this script to make OpenVPN less painless to set up with generating keys and whatnot: [https://github.com/Nyr/openvpn-install](https://github.com/Nyr/openvpn-install) 
My home network is IP'd as 10.13.0.X/24. My VPN network is IP'd as 10.8.0.X/24. 

My goal is this. I want to be able to set up two VPN profiles within Network Manager, one called General and one called Secure. The purpose of the general one is so I can tap into my home network and retrieve files/check on video surveillance/etc while still being able to access local things to the LAN I might be on. The point of the secure profile is to route 100% of my traffic to the secure VPN, which bounces back home, and then out. This would allow me some flexibility, as I can be a little looser with the general profile if I just need to hit home, or I can feel more confident on the secure profile while logging in to my bank when outside of my home wifi. The general one works fine as is, as I simply had to enable "Use This Connection Only For Resources In Its Network" within Network Manager. Okay fine. But the secure one I'm struggling with. Currently the only difference between the two profiles is the checkbox mentioned as well as the DNS server (10.13.0.1) being static'ly assigned on the 'secure' profile.

I was tinkering around a bit and I noticed something. I enabled tethering on my phone, connected my laptop to my phone, VPN'd home using the secure VPN profile, and decided to try something. I unplugged my modem from WAN. Thing is, I expected the connection on my laptop to tank. It didn't. I could still browse and do my thing. Clearly I wasn't routing 100% of my traffic home (or else the 4G just immediately took over), as otherwise my connection would have disconnected then. That said, when I run "route", I noticed that the metric for my VPN was 50, whereas my tethered connection was 600. What is metric? The lower one wins default, I assume? If so, maybe it just continued working because it instantly failed over to my tethered connection when the VPN link went down with my router being unplugged?

Anyway, that was a bit of a random brain dump containing several questions. The root question I'm looking for assistance with is how I can set up the Network Manager VPN profile to route 100% of my traffic (no questions) when using the secure profile. My concern behind this is the fact that my connection remains alive even if my home network (where the VPN server is) goes offline. Think of it like this. I'm on public wifi out somewhere, I activate my secure VPN connection, and seconds later my home network goes down for some reason. I proceed to log in to my bank. Well, what just happened? Since A) the connection keeps working, and ***B***), my network manager icon in the upper corner *still* shows my VPN icon to suggest I'm connected (why is this?), I can only imagine that I just sent my banking info over an insecure line. If the Network Manager VPN icon would disappear the instant my VPN server is inaccessible I would have less of an issue with it, but eh... doesn't seem to be the case.

Anyway, just some mixed thoughts, questions, etc. Curious if anybody can make sense of my cryptic post and help me confirm a few things. I would appreciate any and all insight. Thanks. :)

EDIT - Something I'm noticing is this. If I tether my laptop to my phone, then select either the 'secure' VPN *or* the general VPN profile, either way my external IP address is an IPv6 address provided by my 4G connection on my phone. In both scenarios, my external IP does not reflect my IPv4 address of my house where the VPN server resides.

Googling says I need to push redirect-gateway. And I did. And there's no change. I'm not understanding why?

---

### Post by Roasted on 2017-09-04
With some tinkering today, I think I found what was causing a good portion of the confusion. My phone sometimes (not always, from what I can see) pulls an IPv6 address. My ISP provides my house with an IPv4 address. In the instances where my phone pulls an IPv4 address, I get (let's say) 210.x.x.x. With my laptop tethered to my phone with the 210.x.x.x IP, if I activate the VPN, it yields a 170.x.x.x IP -- same as my house. Nice!

If I reboot my phone a few times and pick up an IPv6 address, my VPN works in the sense that I *can* access things internally to my home network, however my public-facing IP doesn't change to reflect home.

So I guess what I need to do is look into how do-able it is to integrate IPv4 and IPv6 with OpenVPN, as my ISP is not providing IPv6 addresses at the moment. If I can figure this out, it would make for less of a headache if I ever find myself out-and-about on an IPv6 network and I want to tunnel everything (*everything*) home.

So in short, when my phone pulls an IPv4, my laptop yields a change in public IP to reflect my IP from home. Good.
But when my phone pulls an IPv6, it never changes the public IP to reflect home -- it continues to show my public IP as the v6 address from my phone's ISP. Meh. I can still hit internal resources to my home network, it just never reflects my home public IP as the public IP of my VPN connection when the phone is linked up via IPv6.

Figured I'd add some configs below in case it helps.

/etc/sysctl.conf entry that was edited:
```
# Uncomment the next line to enable packet forwarding for IPv4
net.ipv4.ip_forward=1

```

/etc/openvpn/server.conf:
```
administrator@web:~$ cat /etc/openvpn/server.conf
port 443
proto udp
dev tun
sndbuf 0
rcvbuf 0
ca ca.crt
cert server.crt
key server.key
dh dh.pem
tls-auth ta.key 0
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "dhcp-option DNS 10.8.0.1"
#push "dhcp-option DNS 8.8.8.8"
#push "dhcp-option DNS 8.8.4.4"
keepalive 10 120
cipher AES-256-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem
push "route 10.13.0.0 255.255.255.0"
push "redirect-gateway def1"

```

Server ifconfig:
```
administrator@web:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:1295 (1.2 KB)  TX bytes:1295 (1.2 KB)

p1p1      Link encap:Ethernet  HWaddr 72:d3:25:16:3c:6c  
          inet addr:10.13.0.201  Bcast:10.13.0.255  Mask:255.255.255.0
          inet6 addr: fe80::76d4:35ff:fe16:3c6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7468 errors:0 dropped:9 overruns:0 frame:0
          TX packets:5119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2554624 (2.5 MB)  TX bytes:1868814 (1.8 MB)

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:1358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1466 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:156077 (156.0 KB)  TX bytes:901785 (901.7 KB)

```

IPtables output on server:
```
administrator@web:~$ sudo iptables -t nat -L --line-numbers -n
[sudo] password for administrator: 
Chain PREROUTING (policy ACCEPT)
num  target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
num  target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
num  target     prot opt source               destination         
1    SNAT       all  --  10.8.0.0/24          0.0.0.0/0            to:10.13.0.201
2    SNAT       all  --  10.8.0.0/24          0.0.0.0/0            to:10.13.0.201

```

The SNAT entry came from [https://openvpn.net/index.php/open-source/documentation/howto.html#redirect](https://openvpn.net/index.php/open-source/documentation/howto.html#redirect) 

Client .ovpn file that I imported to Network Manager:
```
client
dev tun
proto udp
sndbuf 0
rcvbuf 0
remote MYDOMAIN 443
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
cipher AES-256-CBC
comp-lzo
#setenv opt block-outside-dns
key-direction 1
verb 3
redirect-gateway def1

```

---

