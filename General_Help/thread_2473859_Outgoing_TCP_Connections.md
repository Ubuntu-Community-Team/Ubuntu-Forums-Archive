---
title: "Outgoing TCP Connections"
date: 2022-04-16
forum: General Help
---

### Post by Quarkrad on 2022-04-16
A recent ubuntu-mate email gave a terminal command that shows outgoing tcp connections.
```
ss -t -o state established '( dport = :443 || dport = :80 )' | grep -Po '([0-9a-z:.]*)(?=:http[s])' | sort -u|netcat whois.cymru.com 43|grep -v "AS Name"|sort -t'|' -k3
```

I have set my ff browser to **ubuntuforums.org** as the opening page and get the following output from the command above:

```
dad@dadubuntu:~$ ss -t -o state established '( dport = :443 || dport = :80 )' | grep -Po '([0-9a-z:.]*)(?=:http[s])' | sort -u|netcat whois.cymru.com 43|grep -v "AS Name"|sort -t'|' -k3
16509   | 52.41.98.34      | AMAZON-02, US
396982  | 34.117.237.239   | GOOGLE-CLOUD-PLATFORM, US
396982  | 34.120.115.102   | GOOGLE-CLOUD-PLATFORM, US
396982  | 34.120.208.123   | GOOGLE-CLOUD-PLATFORM, US
396982  | 34.120.237.76    | GOOGLE-CLOUD-PLATFORM, US
15169   | 142.250.200.14   | GOOGLE, US
63949   | 139.162.215.242  | LINODE-AP Linode, LLC, US

```

I am surprised at this output as I have no association with Amazon or Google Cloud.  Any feedback on why these connections are being made would be appreciated.  My dns entry for my vpn connection is 162.252.172.57.

---

### Post by The Cog on 2022-04-16
Both google and amazon do a lot of hosting - they allow other companies to run web servers on their network (for a fee of course). So this only tells you who the hosting service provider is.
I don't know how you might go about who is leasing that particular IP/server.

It may be better to log all the DNS name lookup requests issued by your computer. I dont' actually know of a good simple utility to do that though.

---

### Post by TheFu on 2022-04-16
What sort of blocking - network and advertising and malware - are you doing today?
For many people, having a pi-hole as their local DNS is a reasonable way to stop those sorts of things.  With the pi-hjole logs, we can see the dns lookup and the resulting IP. Filtering the logs for both/either provides answers you seek.

This is also why running a firewall on your computer(s) and not just at the router is so important.  Blocking all inbound and most outbound is a first step.

There is an end-user firewall tool that do lots of logging too.  [https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/](https://www.cyberciti.biz/python-tutorials/opensnitch-the-little-snitch-application-like-firewall-tool-for-linux/)  OpenSnitch.  I don't think it is any of the repos.  Might be worth a look.

---

### Post by Quarkrad on 2022-04-16
In terms of add-ons I use noscript, ghostery, privacy badger

---

### Post by TheFu on 2022-04-16
Any outbound firewall rules?
Any dns filtering?
How do you handle things outside a browser or for all the other browsers?

---

### Post by Quarkrad on 2022-04-16
This is my iptables:

```
dad@dadubuntu:~$ sudo iptables -L -n
[sudo] password for dad: 
Chain INPUT (policy DROP)
target     prot opt source               destination         
LIBVIRT_INP  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-input  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain FORWARD (policy DROP)
target     prot opt source               destination         
LIBVIRT_FWX  all  --  0.0.0.0/0            0.0.0.0/0           
LIBVIRT_FWI  all  --  0.0.0.0/0            0.0.0.0/0           
LIBVIRT_FWO  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-forward  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
LIBVIRT_OUT  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-before-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-after-logging-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-reject-output  all  --  0.0.0.0/0            0.0.0.0/0           
ufw-track-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain LIBVIRT_FWI (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            192.168.122.0/24     ctstate RELATED,ESTABLISHED
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWO (1 references)
target     prot opt source               destination         
ACCEPT     all  --  192.168.122.0/24     0.0.0.0/0           
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain LIBVIRT_FWX (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain LIBVIRT_INP (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:67

Chain LIBVIRT_OUT (1 references)
target     prot opt source               destination         
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:68

Chain ufw-after-forward (1 references)
target     prot opt source               destination         

Chain ufw-after-input (1 references)
target     prot opt source               destination         
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:137
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:138
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:139
ufw-skip-to-policy-input  tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:445
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:67
ufw-skip-to-policy-input  udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:68
ufw-skip-to-policy-input  all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST

Chain ufw-after-logging-forward (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-input (1 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-after-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-after-output (1 references)
target     prot opt source               destination         

Chain ufw-before-forward (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ufw-user-forward  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-input (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
DROP       all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 3
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 11
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 12
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp spt:67 dpt:68
ufw-not-local  all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     udp  --  0.0.0.0/0            224.0.0.251          udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            239.255.255.250      udp dpt:1900
ufw-user-input  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-before-logging-forward (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-input (1 references)
target     prot opt source               destination         

Chain ufw-before-logging-output (1 references)
target     prot opt source               destination         

Chain ufw-before-output (1 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0            ctstate RELATED,ESTABLISHED
ufw-user-output  all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-logging-allow (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW ALLOW] "

Chain ufw-logging-deny (2 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ctstate INVALID limit: avg 3/min burst 10
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10 LOG flags 0 level 4 prefix "[UFW BLOCK] "

Chain ufw-not-local (1 references)
target     prot opt source               destination         
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type LOCAL
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type MULTICAST
RETURN     all  --  0.0.0.0/0            0.0.0.0/0            ADDRTYPE match dst-type BROADCAST
ufw-logging-deny  all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 10
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-reject-forward (1 references)
target     prot opt source               destination         

Chain ufw-reject-input (1 references)
target     prot opt source               destination         

Chain ufw-reject-output (1 references)
target     prot opt source               destination         

Chain ufw-skip-to-policy-forward (0 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-input (7 references)
target     prot opt source               destination         
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-skip-to-policy-output (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-track-forward (1 references)
target     prot opt source               destination         

Chain ufw-track-input (1 references)
target     prot opt source               destination         

Chain ufw-track-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            ctstate NEW

Chain ufw-user-forward (1 references)
target     prot opt source               destination         

Chain ufw-user-input (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53864
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53864
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:22
ACCEPT     tcp  --  192.168.1.150        192.168.1.150        tcp spt:5438 dpt:5438
ACCEPT     udp  --  192.168.1.150        192.168.1.150        udp spt:5438 dpt:5438
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:32400
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32400
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1900
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32410
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32412
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32413
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32414
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:32469

Chain ufw-user-limit (0 references)
target     prot opt source               destination         
LOG        all  --  0.0.0.0/0            0.0.0.0/0            limit: avg 3/min burst 5 LOG flags 0 level 4 prefix "[UFW LIMIT BLOCK] "
REJECT     all  --  0.0.0.0/0            0.0.0.0/0            reject-with icmp-port-unreachable

Chain ufw-user-limit-accept (0 references)
target     prot opt source               destination         
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           

Chain ufw-user-logging-forward (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-input (0 references)
target     prot opt source               destination         

Chain ufw-user-logging-output (0 references)
target     prot opt source               destination         

Chain ufw-user-output (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:53864
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:53864
ACCEPT     tcp  --  192.168.1.150        192.168.1.150        tcp spt:5438 dpt:5438
ACCEPT     udp  --  192.168.1.150        192.168.1.150        udp spt:5438 dpt:5438
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:1900
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:5353
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32410
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32412
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32413
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0            udp dpt:32414
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0            tcp dpt:32469
```

Most of the rules are for a plex server I'm having a little trouble with - about to put a new post in Multimedia, although I do not think the issue is with the ip rules.

I do not believe (newbie in this area) have any DNS filtering

Not sure what you mean by - How do you handle things outside a browser or for all the other browsers

---

### Post by TheFu on 2022-04-16
All sorts of programs make internet connections, not just firefox.  Those browser addons are for 1 browser only.  Other browsers and all the other programs that connect to the internet aren't helped.  That's why I mentioned that.

Also, I'm really worried about the completely open UDP rules.  I doubt any are necessary. Just allow everything from the client to the server in and block everything else.
Appears you use ufw and not iptables directly.  ufs status would be easier to read, since most of the rules are ufw standard stuff.

---

### Post by #&amp;thj^% on 2022-04-16
> **TheFu said:**
>  OpenSnitch.  I don't think it is any of the repos.  Might be worth a look.

+1 Can't say enough good about it. worth a big look. ;)
And some basic usage and more info: [https://github.com/evilsocket/opensnitch/wiki/Configurations](https://github.com/evilsocket/opensnitch/wiki/Configurations)

---

