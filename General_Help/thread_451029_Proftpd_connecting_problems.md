---
title: "Proftpd connecting problems"
date: 2007-05-21
forum: General Help
---

### Post by mazki516 on 2007-05-21
HI Evryone,

i'm trying to make my computer to a server, but i've few problems with proftpd,
i can connect the account from internal ip(i mean local ip - another computer at home), but when i'm trying to connect via my ip address(who provided me by the ISP), it's acually do "Connecting"....for hours :P....i set the ports at the router, and i did it the same way i did when i opend the apache ports, who actually works right now, somebody have a clue why is that? why i can connect from outside?
thanks!

and thank you all about the help from the prevuies theard i've posted!:o
mazki...

edit:
ho sorry i almost forgat, i opend a regular user, gave him alllll the privilages! and i still cannot upload files with him! and when i'm connecting from the master user(not the root, the user i configure at the installation) i can upload... :\  ?

---

### Post by mazki516 on 2007-05-23
someone? :/

---

### Post by fanatik on 2007-05-23
do you have iptables firewall set up to block port 20/21 ?

---

### Post by fanatik on 2007-05-23
did you configure it to run as a standalone server or as part of inetd/xinetd ?

---

### Post by seamuso on 2007-05-23
mazki516,  have you run in a terminal and watched the connection from the real IP? Is the connection attempt even making it to the your system?

like before, in the terminal ....

sudo /etc/init.d/proftpd stop
sudo proftpd -n

then try and login from the main IP and see what info shows about the connection in the terminal.

The timeouts I was seeing with mine were happening on my internal network (computer a -> computer b), but it sounds like that part is working correctly from what you said ..

> i can connect the account from internal ip(i mean local ip - another computer at home)

What router are you using? Does it have any kind of builtin ftp functions that might be intercepting the connection? For instance, the zyxel I used to use has an ftp remote management option.

---

### Post by mazki516 on 2007-05-23
hi all!

proftpd is running as standalone, i really don't know about the iptables firewall, where i can turn it off?, and when i sudo  proftpd -n  with not-local ip address i see that every thing is fine....after 2 min i get "timeout"....and that it...i think that the problem is in the firewall of the UBUNTU, if there is one...
(by the way i've  Dlink, and the config is fine, i can connect on port 21 from outside...)

THANKS! 
mazki

---

### Post by seamuso on 2007-05-23
Have you had someone else try to connect to it? Since it's going through a router, have you set up passive ports and forwarded those also? Have you also forwarded port 20?

here's what mine looks like in my IPCop (last 4)


[http://info.bluefrogcs.com/images/ipcop.png](http://info.bluefrogcs.com/images/ipcop.png)

---

### Post by mazki516 on 2007-05-23
in Dlink it's doesn't work that way...you've Virtual Server, you just need to write the port and the computer ip in the local network and that it, and it's work..
and it's work for Apache...

---

### Post by mazki516 on 2007-05-23
well, if its cause by the firewall of ubuntu, how can i cancel it? turn it off? something?

thanks

---

### Post by seamuso on 2007-05-23
in a terminal 

sudo iptables -L

do you get this?
```
seamuso@bluebuntu:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```That's with no firewall -

or something more like this
```
root@bluerouter:~ # iptables -L | more
Chain BADTCP (2 references)
target     prot opt source               destination
PSCAN      tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG
PSCAN      tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE
PSCAN      tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN
PSCAN      tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST
PSCAN      tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN
NEWNOTSYN  tcp  --  anywhere             anywhere            tcp flags:!FIN,SYN,RST,ACK/SYN state NEW

Chain BOT_FORWARD (1 references)
target     prot opt source               destination

Chain BOT_INPUT (1 references)
target     prot opt source               destination

Chain CUSTOMFORWARD (1 references)
target     prot opt source               destination
BOT_FORWARD  all  --  anywhere             anywhere
LOG        all  --  38.119.38.151        anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  38.119.38.151        anywhere
LOG        all  --  anywhere             38.119.38.151       LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             38.119.38.151
LOG        all  --  38.119.38.152        anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  38.119.38.152        anywhere
LOG        all  --  anywhere             38.119.38.152       LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             38.119.38.152
LOG        all  --  63.150.153.24        anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  63.150.153.24        anywhere
LOG        all  --  anywhere             63.150.153.24       LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             63.150.153.24
LOG        all  --  63.236.38.24         anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  63.236.38.24         anywhere
LOG        all  --  anywhere             63.236.38.24        LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             63.236.38.24
LOG        all  --  63.236.56.243        anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  63.236.56.243        anywhere
LOG        all  --  anywhere             63.236.56.243       LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             63.236.56.243
LOG        all  --  165.193.22.75        anywhere            LOG level warning prefix `banish-forward '
DROP       all  --  165.193.22.75        anywhere
LOG        all  --  anywhere             165.193.22.75       LOG level warning prefix `banish-forward '
DROP       all  --  anywhere             165.193.22.75

Chain CUSTOMINPUT (1 references)
target     prot opt source               destination
BOT_INPUT  all  --  anywhere             anywhere
LOG        all  --  38.119.38.151        anywhere            LOG level warning prefix `banish-input '
DROP       all  --  38.119.38.151        anywhere
LOG        all  --  38.119.38.152        anywhere            LOG level warning prefix `banish-input '
DROP       all  --  38.119.38.152        anywhere
LOG        all  --  63.150.153.24        anywhere            LOG level warning prefix `banish-input '
DROP       all  --  63.150.153.24        anywhere
LOG        all  --  63.236.38.24         anywhere            LOG level warning prefix `banish-input '
DROP       all  --  63.236.38.24         anywhere
LOG        all  --  63.236.56.243        anywhere            LOG level warning prefix `banish-input '
DROP       all  --  63.236.56.243        anywhere
LOG        all  --  165.193.22.75        anywhere            LOG level warning prefix `banish-input '
DROP       all  --  165.193.22.75        anywhere

Chain CUSTOMOUTPUT (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             38.119.38.151       LOG level warning prefix `banish-output '
DROP       all  --  anywhere             38.119.38.151
LOG        all  --  anywhere             38.119.38.152       LOG level warning prefix `banish-output '
DROP       all  --  anywhere             38.119.38.152
LOG        all  --  anywhere             63.150.153.24       LOG level warning prefix `banish-output '
DROP       all  --  anywhere             63.150.153.24
LOG        all  --  anywhere             63.236.38.24        LOG level warning prefix `banish-output '
DROP       all  --  anywhere             63.236.38.24
LOG        all  --  anywhere             63.236.56.243       LOG level warning prefix `banish-output '
DROP       all  --  anywhere             63.236.56.243
LOG        all  --  anywhere             165.193.22.75       LOG level warning prefix `banish-output '
DROP       all  --  anywhere             165.193.22.75

Chain DHCPBLUEINPUT (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:bootpc dpt:bootps
ACCEPT     udp  --  anywhere             anywhere            udp spt:bootpc dpt:bootps

Chain DMZHOLES (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  lfs-laptop.bluefrogcs.com  blue-store.bluefrogcs.com tcp dpt:ssh
ACCEPT     tcp  --  lfs-laptop.bluefrogcs.com  big-blue-lfs.bluefrogcs.com tcp dpt:ssh
ACCEPT     tcp  --  lfs-laptop.bluefrogcs.com  blue-store.bluefrogcs.com tcp dpt:http
ACCEPT     tcp  --  lfs-laptop.bluefrogcs.com  big-blue-lfs.bluefrogcs.com tcp dpt:http

Chain GUIINPUT (1 references)
target     prot opt source               destination
ACCEPT     icmp --  anywhere             anywhere            icmp echo-request

Chain INPUT (policy DROP)
target     prot opt source               destination
ipac~o     all  --  anywhere             anywhere
BADTCP     all  --  anywhere             anywhere
CUSTOMINPUT  all  --  anywhere             anywhere
GUIINPUT   all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED,ESTABLISHED
IPSECVIRTUAL  all  --  anywhere             anywhere

```

---

### Post by mazki516 on 2007-05-23
the first example...no firewall at all :/
and the router is realy fine :/

---

### Post by fanatik on 2007-05-24
> **seamuso said:**
> Have you had someone else try to connect to it? Since it's going through a router, have you set up passive ports and forwarded those also? Have you also forwarded port 20?

so you have checked you have both port 20 and 21 forwarded to your pc?

---

### Post by mazki516 on 2007-05-24
yes...i forwarded both ports....anything :/
there is some guide out there to make intenet connection? i mean connect by my self and not from the router...(modem drivers are not neccessery...)

---

