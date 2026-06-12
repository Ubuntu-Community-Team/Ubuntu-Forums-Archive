---
title: "Can not ping VPS"
date: 2014-11-21
forum: General Help
---

### Post by Simon_Whiteley on 2014-11-21
Hi guys!

I have a small VPS running Ubuntu 14.04 LTS. 
Last night I decided to to try and install OpenVPN- access server, and it was actually pretty easy. 
I can use OpenVPN without any problems.
I think it has messed with my iptables a bit though, because I cannot seem to ping my ip address anymore.
Every time it seems to fail by timing out. Almost seems like ICMP input is blocked.


I'm kind of having a hard time troubleshooting this. I tried flushing iptables and my friend suggested installing csf since apparently that is a easier way to work with iptables (i have no idea if this has any truth to it) but I have not managed to have any success so far.

How should I proceed?

EDIT:
I tried csf and ran 
csf -r
iptables -L

> 

root@server:~# csf -r
Flushing chain `INPUT'
Flushing chain `FORWARD'
Flushing chain `OUTPUT'
Flushing chain `PREROUTING'
Flushing chain `INPUT'
Flushing chain `OUTPUT'
Flushing chain `POSTROUTING'
Flushing chain `INPUT'
Flushing chain `FORWARD'
Flushing chain `OUTPUT'
csf: FASTSTART loading DROP no logging (IPv4)
csf: FASTSTART loading DROP no logging (IPv6)
LOG  tcp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *TCP_IN Blocked* "
LOG  tcp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   tcp flags:0x17/0x02 limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *TCP_OUT Blocked* "
LOG  udp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *UDP_IN Blocked* "
LOG  udp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *UDP_OUT Blocked* "
LOG  icmp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *ICMP_IN Blocked* "
LOG  icmp opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0   limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *ICMP_OUT Blocked* "
LOG  tcp opt    in * out *  ::/0  -> ::/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *TCP6IN Blocked* "
LOG  tcp opt    in * out *  ::/0  -> ::/0   tcp flags:0x17/0x02 limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *TCP6OUT Blocked* "
LOG  udp opt    in * out *  ::/0  -> ::/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *UDP6IN Blocked* "
LOG  udp opt    in * out *  ::/0  -> ::/0   limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *UDP6OUT Blocked* "
LOG  icmpv6 opt    in * out *  ::/0  -> ::/0   limit: avg 30/min burst 5 LOG flags 0 level 4 prefix "Firewall: *ICMP6IN Blocked* "
LOG  icmpv6 opt    in * out *  ::/0  -> ::/0   limit: avg 30/min burst 5 LOG flags 8 level 4 prefix "Firewall: *ICMP6OUT Blocked* "
DROP  all opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0
DROP  all opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0
DROP  all opt    in * out *  ::/0  -> ::/0
DROP  all opt    in * out *  ::/0  -> ::/0
DENYOUT  all opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0
DENYIN  all opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0
ALLOWOUT  all opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0
ALLOWIN  all opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0
DENYOUT  all opt    in * out !lo  ::/0  -> ::/0
DENYIN  all opt    in !lo out *  ::/0  -> ::/0
ALLOWOUT  all opt    in * out !lo  ::/0  -> ::/0
ALLOWIN  all opt    in !lo out *  ::/0  -> ::/0
csf: FASTSTART loading Packet Filter (IPv4)
csf: FASTSTART loading Packet Filter (IPv6)
DROP  all opt -- in * out *  0.0.0.0/0  -> 0.0.0.0/0
INVALID  tcp opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0
INVALID  tcp opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0
DROP  all opt    in * out *  ::/0  -> ::/0
INVALID  tcp opt    in !lo out *  ::/0  -> ::/0
INVALID  tcp opt    in * out !lo  ::/0  -> ::/0
csf: FASTSTART loading csf.allow (IPv4)
ACCEPT  all opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0   ctstate RELATED,ESTABLISHED
ACCEPT  all opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0   ctstate RELATED,ESTABLISHED
ACCEPT  all opt    in !lo out *  ::/0  -> ::/0   ctstate RELATED,ESTABLISHED
ACCEPT  all opt    in * out !lo  ::/0  -> ::/0   ctstate RELATED,ESTABLISHED
csf: FASTSTART loading TCP_IN (IPv4)
csf: FASTSTART loading TCP6_IN (IPv6)
csf: FASTSTART loading TCP_OUT (IPv4)
csf: FASTSTART loading TCP6_OUT (IPv6)
csf: FASTSTART loading UDP_IN (IPv4)
csf: FASTSTART loading UDP6_IN (IPv6)
csf: FASTSTART loading UDP_OUT (IPv4)
csf: FASTSTART loading UDP6_OUT (IPv6)
ACCEPT  icmp opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0   icmptype 8 limit: avg 1/sec burst 5
ACCEPT  icmp opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0   icmptype 0
ACCEPT  icmp opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0   icmptype 8
ACCEPT  icmp opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0   icmptype 0 limit: avg 1/sec burst 5
ACCEPT  icmp opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0   icmptype 11
ACCEPT  icmp opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0   icmptype 3
ACCEPT  icmp opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0   icmptype 11
ACCEPT  icmp opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0   icmptype 3
ACCEPT  icmpv6 opt    in !lo out *  ::/0  -> ::/0
ACCEPT  icmpv6 opt    in * out !lo  ::/0  -> ::/0
ACCEPT  all opt -- in lo out *  0.0.0.0/0  -> 0.0.0.0/0
ACCEPT  all opt -- in * out lo  0.0.0.0/0  -> 0.0.0.0/0
LOGDROPOUT  all opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0
LOGDROPIN  all opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0
ACCEPT  all opt    in lo out *  ::/0  -> ::/0
ACCEPT  all opt    in * out lo  ::/0  -> ::/0
LOGDROPOUT  all opt    in * out !lo  ::/0  -> ::/0
LOGDROPIN  all opt    in !lo out *  ::/0  -> ::/0
csf: FASTSTART loading DNS (IPv4)
csf: FASTSTART loading DNS (IPv6)
LOCALOUTPUT  all opt -- in * out !lo  0.0.0.0/0  -> 0.0.0.0/0
LOCALINPUT  all opt -- in !lo out *  0.0.0.0/0  -> 0.0.0.0/0
LOCALOUTPUT  all opt    in * out !lo  ::/0  -> ::/0
LOCALINPUT  all opt    in !lo out *  ::/0  -> ::/0
*WARNING* TESTING mode is enabled - do not forget to disable it in the configuration


*WARNING* RESTRICT_SYSLOG is disabled. See SECURITY WARNING in /etc/csf/csf.conf.

And iptables

> root@server:~# iptables -L
Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  v2.pcextreme.nl      anywhere             tcp dpt:domain
ACCEPT     udp  --  v2.pcextreme.nl      anywhere             udp dpt:domain
ACCEPT     tcp  --  v2.pcextreme.nl      anywhere             tcp spt:domain
ACCEPT     udp  --  v2.pcextreme.nl      anywhere             udp spt:domain
ACCEPT     tcp  --  rn1.pcextreme.nl     anywhere             tcp dpt:domain
ACCEPT     udp  --  rn1.pcextreme.nl     anywhere             udp dpt:domain
ACCEPT     tcp  --  rn1.pcextreme.nl     anywhere             tcp spt:domain
ACCEPT     udp  --  rn1.pcextreme.nl     anywhere             udp spt:domain
LOCALINPUT  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere
INVALID    tcp  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:imap2
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:urd
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:submission
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:943
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:openvpn
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:20
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:fsp
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:domain
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request limit: avg 1/sec burst 5
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply limit: avg 1/sec burst 5
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
LOGDROPIN  all  --  anywhere             anywhere


Chain FORWARD (policy DROP)
target     prot opt source               destination


Chain OUTPUT (policy DROP)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             v2.pcextreme.nl      tcp dpt:domain
ACCEPT     udp  --  anywhere             v2.pcextreme.nl      udp dpt:domain
ACCEPT     tcp  --  anywhere             v2.pcextreme.nl      tcp spt:domain
ACCEPT     udp  --  anywhere             v2.pcextreme.nl      udp spt:domain
ACCEPT     tcp  --  anywhere             rn1.pcextreme.nl     tcp dpt:domain
ACCEPT     udp  --  anywhere             rn1.pcextreme.nl     udp dpt:domain
ACCEPT     tcp  --  anywhere             rn1.pcextreme.nl     tcp spt:domain
ACCEPT     udp  --  anywhere             rn1.pcextreme.nl     udp spt:domain
LOCALOUTPUT  all  --  anywhere             anywhere
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             udp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             tcp spt:domain
ACCEPT     udp  --  anywhere             anywhere             udp spt:domain
ACCEPT     all  --  anywhere             anywhere
INVALID    tcp  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere             ctstate RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ftp-data
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ftp
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:ssh
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:smtp
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:domain
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:pop3
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:auth
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:https
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:imaps
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:pop3s
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:943
ACCEPT     tcp  --  anywhere             anywhere             ctstate NEW tcp dpt:openvpn
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:20
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:fsp
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:domain
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:113
ACCEPT     udp  --  anywhere             anywhere             ctstate NEW udp dpt:ntp
ACCEPT     icmp --  anywhere             anywhere             icmp echo-reply
ACCEPT     icmp --  anywhere             anywhere             icmp echo-request
ACCEPT     icmp --  anywhere             anywhere             icmp time-exceeded
ACCEPT     icmp --  anywhere             anywhere             icmp destination-unreachable
LOGDROPOUT  all  --  anywhere             anywhere


Chain ALLOWIN (1 references)
target     prot opt source               destination
ACCEPT     all  --  myip  anywhere
ACCEPT     all  --  anotherip       anywhere


Chain ALLOWOUT (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             e142239.upc-e.chello.nl
ACCEPT     all  --  anywhere             145.89.162.194


Chain DENYIN (1 references)
target     prot opt source               destination


Chain DENYOUT (1 references)
target     prot opt source               destination


Chain INVALID (2 references)
target     prot opt source               destination
INVDROP    all  --  anywhere             anywhere             ctstate INVALID
INVDROP    tcp  --  anywhere             anywhere             tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE
INVDROP    tcp  --  anywhere             anywhere             tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG
INVDROP    tcp  --  anywhere             anywhere             tcp flags:FIN,SYN/FIN,SYN
INVDROP    tcp  --  anywhere             anywhere             tcp flags:SYN,RST/SYN,RST
INVDROP    tcp  --  anywhere             anywhere             tcp flags:FIN,RST/FIN,RST
INVDROP    tcp  --  anywhere             anywhere             tcp flags:FIN,ACK/FIN
INVDROP    tcp  --  anywhere             anywhere             tcp flags:PSH,ACK/PSH
INVDROP    tcp  --  anywhere             anywhere             tcp flags:ACK,URG/URG
INVDROP    tcp  --  anywhere             anywhere             tcp flags:!FIN,SYN,RST,ACK/SYN ctstate NEW


Chain INVDROP (10 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere


Chain LOCALINPUT (1 references)
target     prot opt source               destination
ALLOWIN    all  --  anywhere             anywhere
DENYIN     all  --  anywhere             anywhere


Chain LOCALOUTPUT (1 references)
target     prot opt source               destination
ALLOWOUT   all  --  anywhere             anywhere
DENYOUT    all  --  anywhere             anywhere


Chain LOGDROPIN (1 references)
target     prot opt source               destination
DROP       tcp  --  anywhere             anywhere             tcp dpt:bootps
DROP       udp  --  anywhere             anywhere             udp dpt:bootps
DROP       tcp  --  anywhere             anywhere             tcp dpt:bootpc
DROP       udp  --  anywhere             anywhere             udp dpt:bootpc
DROP       tcp  --  anywhere             anywhere             tcp dpt:sunrpc
DROP       udp  --  anywhere             anywhere             udp dpt:sunrpc
DROP       tcp  --  anywhere             anywhere             tcp dpt:auth
DROP       udp  --  anywhere             anywhere             udp dpt:113
DROP       tcp  --  anywhere             anywhere             tcp dpts:loc-srv:netbios-ssn
DROP       udp  --  anywhere             anywhere             udp dpts:loc-srv:netbios-ssn
DROP       tcp  --  anywhere             anywhere             tcp dpt:microsoft-ds
DROP       udp  --  anywhere             anywhere             udp dpt:microsoft-ds
DROP       tcp  --  anywhere             anywhere             tcp dpt:isakmp
DROP       udp  --  anywhere             anywhere             udp dpt:isakmp
DROP       tcp  --  anywhere             anywhere             tcp dpt:login
DROP       udp  --  anywhere             anywhere             udp dpt:who
DROP       tcp  --  anywhere             anywhere             tcp dpt:520
DROP       udp  --  anywhere             anywhere             udp dpt:route
LOG        tcp  --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning prefix "Firewall: *TCP_IN Blocked* "
LOG        udp  --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning prefix "Firewall: *UDP_IN Blocked* "
LOG        icmp --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning prefix "Firewall: *ICMP_IN Blocked* "
DROP       all  --  anywhere             anywhere


Chain LOGDROPOUT (1 references)
target     prot opt source               destination
LOG        tcp  --  anywhere             anywhere             tcp flags:FIN,SYN,RST,ACK/SYN limit: avg 30/min burst 5 LOG level warning uid prefix "Firewall: *TCP_OUT Blocked* "
LOG        udp  --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning uid prefix "Firewall: *UDP_OUT Blocked* "
LOG        icmp --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning uid prefix "Firewall: *ICMP_OUT Blocked* "
DROP       all  --  anywhere             anywhere

It does indeed say "LOG        icmp --  anywhere             anywhere             limit: avg 30/min burst 5 LOG level warning prefix "Firewall: *ICMP_IN Blocked* ""

Maybe I should add that I'm running a webserver that's working like a charm, so for some reason I just can't ping it.

---

### Post by nerdtron on 2014-11-21
You are already connected to the OpenVPN server? and your computer is already the client?
Can you ping the vpn IP of the server? But can't ping the public IP?

What is the output of "route -n" from your computer?

---

### Post by Simon_Whiteley on 2014-11-21
No, I can't ping my VPS' external IP adress, time-outs every time.


Here's the "route -n"
> 


root@server:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         185.66.248.3    0.0.0.0         UG    0      0        0 eth0
172.27.224.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t0
172.27.228.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t1
172.27.232.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t2
172.27.236.0    0.0.0.0         255.255.252.0   U     0      0        0 as0t3
185.66.248.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0


I dont know what to do to allow the ping, some firewall is blocking it I guess

>   1    <1 ms    <1 ms    <1 ms  192.168.0.1  2    30 ms     5 ms     6 ms  10.15.160.129
  3    13 ms    10 ms    11 ms  212.142.61.197
  4    15 ms    14 ms    15 ms  84.116.244.21
  5    31 ms    14 ms    17 ms  84.116.135.202
  6     9 ms     8 ms    10 ms  adm-b5-link.telia.net [62.115.12.133]
  7    17 ms     9 ms    15 ms  pcextreme-ic-307463-adm-b5.c.telia.net [195.12.2
55.234]
  8    12 ms    14 ms    10 ms  92.63.170.94
  9     *        *        *     Request timed out.
 10     *        *        *     Request timed out.

---

### Post by nerdtron on 2014-11-21
> **Simon_Whiteley said:**
> No, I can't ping my VPS' external IP adress, time-outs every time.


Here's the "route -n"


I dont know what to do to allow the ping, some firewall is blocking it I guess

Is this even connected to the VPN server? It doesn't even even learn the routes to the vpn server I guess.
Plus what is the result of traceroute?
And what is your config for the OpenVPN? tun or tap? Might as well post you openvpn config for both server and client so that we can heve a clear picture here.

---

### Post by nerdtron on 2014-11-21
This is not a firewall issue if you can ping the VPS before you connect to the openvpn. Might be a config issue.

---

### Post by Simon_Whiteley on 2014-11-21
I'm more interesting in why I cannot seem to ping my servers ip from my home ip. Or from my schools ip. 
The OpenVPN part is not that important for me, its just that I suspected that might have messed with the iptables. 

I can connect to the VPN server when I run the client on my windows machine. 
The webserver is also up and I can use nginx and everything, I'm just not sure why when I pull up a cmd prompt and tracert the vpsIP it times out.
I want to server to be pingable, but at the moment it always times out.


Sorry if I was a bit unclear. If this is due to openvpn can i just remove it ?
The server (VPS) ip and openvpn server ip are the same.

---

### Post by Simon_Whiteley on 2014-11-22
> **nerdtron said:**
> Is this even connected to the VPN server? It doesn't even even learn the routes to the vpn server I guess.
Plus what is the result of traceroute?
And what is your config for the OpenVPN? tun or tap? Might as well post you openvpn config for both server and client so that we can heve a clear picture here.
I'm not sure if I'm using tun or tap? Where can i find this? 

Sorry if I come across oblivious but pretty much all I did was install openvpn-as and made a openvpn admin password and i could change some settings via myip:943/admin and download a client via myip:943
OpenVPN client could connect to the openvpn server so I thought it worked okay (i did not do any config changes) but for some reason the public ip of the ubuntu vps cannot be pinged anymore, and i dont like that.

I'd rather just remove the openvpn server and be able to ping my public ip again. I'm not sure how though :(

---

### Post by nerdtron on 2014-11-22
> I'd rather just remove the openvpn server and be able to ping my public ip again. I'm not sure how though

I thought you setup your vpn server manually and created your own config. I'm not familiar with the you installed it and setup.
To see the config file for the openvpn.
```
ps aux | grep vpn
```
That should output the path of the current config in use.

To simply stop the openvpn service.
```
sudo service openvpn stop
```

---

