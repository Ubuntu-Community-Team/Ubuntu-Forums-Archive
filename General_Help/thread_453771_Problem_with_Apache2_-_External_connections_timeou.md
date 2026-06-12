---
title: "Problem with Apache2 - External connections timeout"
date: 2007-05-24
forum: General Help
---

### Post by Scorpuk on 2007-05-24
Not sure when it happened, but I can no longer reach my apache server from a computer outside my LAN.

Any attempt to reach it through my allocated IP address (ISP's) from a computer outside my LAN results in a time out, but on my LAN it works ok.


Running: 

Ubuntu 7.04
Apache/2.2.3 
PHP/5.2.1


Server is connected to Netgear DG834N router and set in the DMZ.


Previously worked 100%.


Server URL: [http://scorpuk.plus.com](http://scorpuk.plus.com)

Router is set to ignore pings!


Any thoughts?

---

### Post by mbradlcu on 2007-05-25
yep it's unreachable:
daturan@matt-x64:~/Xdrive$ telnet 80.229.16.99 80
Trying 80.229.16.99...
note# it didnt' give me a connection refused like port 22, 23 did..
what does 'sudo  iptables -L' give you.

---

### Post by amphet on 2007-05-25
does your ISP allow you to host websites?

---

### Post by Scorpuk on 2007-05-26
Result of sudo iptables -L

> john@HTPC:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


I would imagine 22/23 would give a refused response as SSH is not installed.


As for my ISP allowing it, unless they have changed policy without telling me then yes they do. Up until almost a month ago I had full access to my web server from outside my LAN. (I will raise a ticket with them to find out though)


Tnx.

---

### Post by Scorpuk on 2007-05-26
If someone could try the link again as I found out my ISP activated a firewall on my connection...

---

### Post by mbradlcu on 2007-05-27
I'm not getting a resolve for that addy:
host [http://scorpuk.plus.com](http://scorpuk.plus.com)
Host [http://scorpuk.plus.com](http://scorpuk.plus.com) not found: 3(NXDOMAIN)

got a new IP?

---

### Post by swisstone on 2008-05-09
Hi, was just browsing your forum post about apache not being reachable from external address - I notice you have solved it! Can you advise me what the problem was? I have exactly the same problem (just installed Ubuntu 8.04 Server and vTiger 504, cannot get to it from external addresses) Many thanks.

---

### Post by mbradlcu on 2008-05-09
You may want to try using 'tcptraceroute' (it's not installed by default)
using is really simple, eg:
```

tcptraceroute your_server_IP 80

```

if you see it die at your box, (but I'm guessing it's a router forwarding issue,, then check either 'iptables -L' or 'netstat -upant' although you've indicated you can hit it locally.

---

