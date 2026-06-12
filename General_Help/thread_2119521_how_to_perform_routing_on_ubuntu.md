---
title: "how to perform routing on ubuntu ?"
date: 2013-02-24
forum: General Help
---

### Post by drvirus on 2013-02-24
hi ,
i have centos server with two interfaces
router<======eth0-server-eth1====>ftp server


my request is , 

how to preform routing on the two interfaces of the server ,
i mean how to put a gateway for eth1 of the server to be interface eth0 .???


my question in another view , 
how to access ftp server from router ??
i know how  to do routing on the router , but i need to do it on linux sever with ubuntu ?

with my best regards
[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]

---

### Post by matt_symes on 2013-02-24
> **drvirus said:**
> hi ,
i have centos server with two interfaces
router<======eth0-server-eth1====>ftp server

my request is , 

how to preform routing on the two interfaces of the server ,
i mean how to put a gateway for eth1 of the server to be interface eth0 .???

my question in another view , 
how to access ftp server from router ??
i know how  to do routing on the router , but i need to do it on linux sever with ubuntu ?

with my best regards
[IMG]https://lqo-thequestionsnetw.netdna-ssl.com/questions/images/smilies/smile.gif[/IMG]

Enable ipv4 formarding.

```
sudo nano /etc/sysctl.conf
```add the line or uncomment it if it already there.

```
net.ipv4.ip_forwarding = 1
```Save the file and reboot your PC.

Next add iptables rules.

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```save the rules

```
sudo sh -c "iptables-save > /etc/iptables.rules" 
```and restore the rules at startup you use the command

```
iptables-restore
```for more information about loading the rules at startup then look here.

Kind regards

---

### Post by drvirus on 2013-02-24
> **matt_symes said:**
> Enable ipv4 formarding.

```
sudo nano /etc/sysctl.conf
```add the line or uncomment it if it already there.

```
net.ipv4.ip_forwarding = 1
```Save the file and reboot your PC.

Next add iptables rules.

```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE 
iptables -A FORWARD -i eth0 -o eth1 -m state --state RELATED,ESTABLISHED -j ACCEPT 
iptables -A FORWARD -i eth1 -o eth0 -j ACCEPT
```save the rules

```
sudo sh -c "iptables-save > /etc/iptables.rules" 
```and restore the rules at startup you use the command

```
iptables-restore
```for more information about loading the rules at startup then look here.

Kind regards


hi ,
thanks alot for reply ,
but i dont want it by iptables !

can u help me how to do it by adding config in interface config rather than iptables ?


regards

---

### Post by drvirus on 2013-02-24
my question is , 

how to let an interface to be an exit interface "default route" for another interface ?


regards

---

### Post by matt_symes on 2013-02-24
Hi

> **drvirus said:**
> hi ,
thanks alot for reply ,
but i dont want it by iptables !

Why not use iptables ?

> can u help me how to do it by adding config in interface config rather than iptables ?

regards

Which file are you talking about. Can you be  more specific.

Kind regards

---

