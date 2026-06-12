---
title: "iptables blues."
date: 2005-08-03
forum: General Help
---

### Post by H4rm0ny on 2005-08-03
Hi,

My first post here, hoping someone can rectify my ignorance on some [very] basic network questions:

If you can read this, then I have a working DSL internet connection on ppp0. I want to share this with my laptop (running Kubuntu, same as server) which connects on eth0. After much faffing around, I have frustratedly just set the policies for INPUT, OUTPUT and FORWARD all to ACCEPT, using **iptables**. At this point, I just want to get it working and will refine overkill later.

I followed this with ```
sudo iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
echo "1" > /proc/sys/net/ipv4/ip_forward
``` as cut and pasted from a previous thread. 

I have also set ```
ipforwarding=yes in /etc/network/options
``` on the server.

I've given both computers a fixed IP. The laptop can ping the server. I've also SSH'd to it successfully. What I can't get is anything in the outside world however, i.e. can't ping anything beyond the server, can't use server as proxy for Konqueror etc., etc. 

On the subject of the proxy for Konqueror, I don't get a flat refusal, I just get a timeout.

If anyone can suggest what more needs doing (or more likely what I've done that I shouldn't have), then please let me know. I've been on Kubuntu for a couple of months now, and it knocks the socks off Windows so I hope I haven't found something that it *idoesn't* do better. 

If they have any relevance (I can't tell), I've posted the outputs of iptables at the end. 

Help is really appreciated as I'm convinced I'm just missing something blindingly obvious. Thanks in advance,

-Harmony.

```

root@hoffice:/home/harmony # iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain INBOUND (0 references)
target     prot opt source               destination         

Chain LS (0 references)
target     prot opt source               destination         

Chain NR (0 references)
target     prot opt source               destination         

Chain OUTBOUND (0 references)
target     prot opt source               destination 

root@hoffice:/home/harmony # iptables -t nat --list
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere                      

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by jasmuz on 2005-08-03
If you want a quick fix around it, install "Guidedog"

sudo apt-get install guidedog

With this you will be able to create rules for iptables under a GUI, but do remember to turn on IP_Fowarding on your server to YES.

---

### Post by H4rm0ny on 2005-08-13
Hi,

I got this working, thanks for your help. Guidedog set-up a working configuration for me that was basically what I needed. I've used this as my starting point for ongoing tweaks. 

Would recommend that any complete newb that is having trouble try this. 

Cheers,

-H.

---

