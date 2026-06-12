---
title: "[SOLVED] IP Tables"
date: 2008-05-20
forum: General Help
---

### Post by indiana_crook on 2008-05-20
Does anyone know how to disable IP Tables.  I tried installing firestarter and turning off the firewall, but frostwire still will not connect to the network due to a firewall?  Much thanks!!!

---

### Post by MythosLegend on 2008-05-20
You can flush your ip-tables with
```

iptables -F

```
This will only be temporary until you reboot.

---

### Post by Monicker on 2008-05-20
Are you sure iptables is the problem?


What is the output of the following?

```
sudo iptables -n -L
```

---

### Post by indiana_crook on 2008-05-21
> **Monicker said:**
> Are you sure iptables is the problem?


What is the output of the following?

```
sudo iptables -n -L
```

Chain INPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.1          0.0.0.0/0           tcp flags:!0x17/0x02 
ACCEPT     udp  --  192.168.1.1          0.0.0.0/0           
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
DROP       all  --  0.0.0.0/0            255.255.255.255     
DROP       all  --  0.0.0.0/0            192.168.1.255       
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
LSI        all  -f  0.0.0.0/0            0.0.0.0/0           limit: avg 10/min burst 5 
INBOUND    all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Input' 

Chain FORWARD (policy DROP)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           limit: avg 10/sec burst 5 
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Forward' 

Chain OUTPUT (policy DROP)
target     prot opt source               destination         
ACCEPT     tcp  --  192.168.1.2          192.168.1.1         tcp dpt:53 
ACCEPT     udp  --  192.168.1.2          192.168.1.1         udp dpt:53 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0           
DROP       all  --  224.0.0.0/8          0.0.0.0/0           
DROP       all  --  0.0.0.0/0            224.0.0.0/8         
DROP       all  --  255.255.255.255      0.0.0.0/0           
DROP       all  --  0.0.0.0/0            0.0.0.0             
DROP       all  --  0.0.0.0/0            0.0.0.0/0           state INVALID 
OUTBOUND   all  --  0.0.0.0/0            0.0.0.0/0           
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           LOG flags 0 level 6 prefix `Unknown Output' 

Chain INBOUND (1 references)
target     prot opt source               destination         
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  192.168.1.2          0.0.0.0/0           
ACCEPT     all  --  192.168.1.2          0.0.0.0/0           
LSI        all  --  0.0.0.0/0            0.0.0.0/0           

Chain LOG_FILTER (5 references)
target     prot opt source               destination         

Chain LSI (2 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x02 
LOG        tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       tcp  --  0.0.0.0/0            0.0.0.0/0           tcp flags:0x17/0x04 
LOG        icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 limit: avg 1/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       icmp --  0.0.0.0/0            0.0.0.0/0           icmp type 8 
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Inbound ' 
DROP       all  --  0.0.0.0/0            0.0.0.0/0           

Chain LSO (0 references)
target     prot opt source               destination         
LOG_FILTER  all  --  0.0.0.0/0            0.0.0.0/0           
LOG        all  --  0.0.0.0/0            0.0.0.0/0           limit: avg 5/sec burst 5 LOG flags 0 level 6 prefix `Outbound ' 
REJECT     all  --  0.0.0.0/0            0.0.0.0/0           reject-with icmp-port-unreachable 

Chain OUTBOUND (1 references)
target     prot opt source               destination         
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0           
ACCEPT     tcp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     udp  --  0.0.0.0/0            0.0.0.0/0           state RELATED,ESTABLISHED 
ACCEPT     all  --  0.0.0.0/0            0.0.0.0/0

---

### Post by mrprefect on 2008-05-21
Do these first or you will get locked out as your default policy is DROP

iptables -P INPUT ACCEPT
iptables -P OUTPUT ACCEPT
iptables -P FORWARD ACCEPT

Then do these to flush the tables

iptables -F INPUT
iptables -F OUTPUT
iptables -F FORWARD
iptables -t nat --flush

that should clear most of it.... but this is temporary if they are turning on at start up, you need to find where they are getting run from.

---

### Post by Monicker on 2008-05-21
Okay. Definitely some rules there.  :)  Firestarter is just a front end for iptables.  Just turning off the gui does not reverse the changes it made.  You should change the policy in Firestarter, or use it to add exceptions for Frostwire.  I've never used Frostwire, so I don't specifically what ports it uses by default; I would imagine that is documented in its settings somewhere.

Are you sure you even need a firewall?  Is your machine connected directly to the internet, or is there a router in between?

---

### Post by mrprefect on 2008-05-21
Good question, if there isn't a router and you arn't cheap then go get one. For $50 it is the best 'firewall' investment you can get.... for $100 you can get one that will load a small linux OS that you can do a lot of things with.... 

check out
[http://packetprotector.org/](http://packetprotector.org/)

---

### Post by indiana_crook on 2008-05-21
> **Monicker said:**
> Okay. Definitely some rules there.  :)  Firestarter is just a front end for iptables.  Just turning off the gui does not reverse the changes it made.  You should change the policy in Firestarter, or use it to add exceptions for Frostwire.  I've never used Frostwire, so I don't specifically what ports it uses by default; I would imagine that is documented in its settings somewhere.

Are you sure you even need a firewall?  Is your machine connected directly to the internet, or is there a router in between?

yes I have a router.  Can I just uninstall iptables through synaptic?

Oh, I almost forgot... I'm hard wired not wireless to the router...

---

### Post by Monicker on 2008-05-21
I would just uninstall Firestarter completely, which will remove all of the iptables changes it made.  Make sure that you uninstall firestarter via Synaptic or with apt-get, else its restrictive iptables rules will still be in place.  Then you can just do port forwarding at your routr for the ports which Frostwire needs.

---

### Post by indiana_crook on 2008-05-21
> **Monicker said:**
> I would just uninstall Firestarter completely, which will remove all of the iptables changes it made.  Make sure that you uninstall firestarter via Synaptic or with apt-get, else its restrictive iptables rules will still be in place.  Then you can just do port forwarding at your routr for the ports which Frostwire needs.

Well, I was having this problem before I installed firestarter.  That's why I put it on here.  But I'm not sure how to do port forwarding.  But I've got smart friends...:)

---

### Post by mrprefect on 2008-05-21
port forwarding? doesn't that need to be done on the router?

---

### Post by indiana_crook on 2008-05-21
you see the thing that confusses me, is that Frostwire works great on my Windows computer that is hooked into the same router.  It also worked great on 7.10.  Make sense?

---

### Post by zvacet on 2008-05-21
>  Make sense?

No.Maybe you played with firestarter and changed something.By default ports in Ubuntu are closed fot outside world,meaning they are open to you.If you run app like torrent client in should start working without any tweak with ports.App open port which is needed for it to work.You don´t need Firestarter at all if you use Hardy.You have ufw (uncomplicated firewall).Read [this.]("http://www.ubuntugeek.com/ufw-uncomplicated-firewall-for-ubuntu-hardy.html")

---

