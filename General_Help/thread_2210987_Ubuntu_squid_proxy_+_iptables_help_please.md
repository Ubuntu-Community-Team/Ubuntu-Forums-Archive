---
title: "Ubuntu squid proxy + iptables help please"
date: 2014-03-13
forum: General Help
---

### Post by Exylon on 2014-03-13
Hello everybody,

I want to make a transparent proxy server with squid, which serves as gateway too, so clients of LAN connects to server to go out to the internet and if they go to a banned page, it will block them.

The server have eth1 for LAN and eth2 for NAT and I know how to configure squid but I don't know how IP tables work, how I redirect the clients which enter via port 80 of LAN to NAT? 

If someone could help please, I have tryed many things but I dont understand how iptables work :S.

---

### Post by SeijiSensei on 2014-03-13
Add this rule

```
/sbin/iptables -A PREROUTING -s  your.network/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

Replace "your.network/mask" with the appropriate entry for your internal network like 192.168.1.0/24.  That will grab all traffic from machines in that subnet to remote port 80 and will push it through squid listening on port 3128.

---

### Post by Exylon on 2014-03-13
> **SeijiSensei said:**
> Add this rule

```
/sbin/iptables -A PREROUTING -s  your.network/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

Replace "your.network/mask" with the appropriate entry for your internal network like 192.168.1.0/24.  That will grab all traffic from machines in that subnet to remote port 80 and will push it through squid listening on port 3128.

How I add this rule? 
Just with a command?

If execute it via command line, I get this error: 
"Iptables: No chain/target/match by that name."

:S

---

### Post by SeijiSensei on 2014-03-13
Whoops.  You need to use "-t nat" to write a rule for the PREROUTING chain.  Try this

```
/sbin/iptables -t nat -A PREROUTING -s  your.network/mask -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128
```

Yes, you can run this from the command prompt, though once you test things out, you should add the command to /etc/rc.local so it will be run at boot.

Iptables includes pre-defined "chains" of rules grouped into "tables."  The basic chains, INPUT, OUTPUT and FORWARD are in the default table. Rules that rewrite packets use chains in the "nat" ("network address translation") table; the PREROUTING chain is one such rule.  To write iptables rules for these chains, you need to include the table specifier, in this case "-t nat".

---

### Post by Exylon on 2014-03-14
It isnt working for me....

I will detail what Ive modified here:

nano /etc/network/interfaces:

> auto LAN
iface LAN inet static
address 172.30.2.10
netmask 255.255.255.0

auto WAN
iface WAN inet dhcp 

It working, I can send ping to LAN and to Google at same time, no problem with network.

nano /etc/squid3/squid.conf:

> http_port 3128 transparent

# And uncheck this:
http_access allow localnet

The rest of the file is as default one.

sudo nano /etc/sysctl.conf:

> # Just unchecked this:
net.ipv4.ip_forward=1
net.ipv6.conf.all.forwarding=1

And the last file that Ive modified, sudo nano /etc/rc.local:

> #I add this line:
sbin/iptables -t nat -A PREROUTING -s 172.30.2.0/24 -p tcp -m tcp --dport 80 -j REDIRECT --to-ports 3128

I have a windows xp client connected to server with this LAN  configuration:

> address: 172.30.2.100
netmask: 255.255.255.0
gateway: 172.30.2.10
dns: 8.8.8.8, 8.8.4.4

I can send ping to server but I cant ping [www.google.es(exemple)]("http://www.google.es(exemple)").

Please someone can help me? where is my error?

---

### Post by SeijiSensei on 2014-03-14
Pinging uses an entirely different protocol than web browsing, so squid is irrelevant here.  I suspect you're missing a rule to rewrite outbound packets using "masquerading."  Take a look at this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

---

### Post by Exylon on 2014-03-15
> **SeijiSensei said:**
> Pinging uses an entirely different protocol than web browsing, so squid is irrelevant here.  I suspect you're missing a rule to rewrite outbound packets using "masquerading."  Take a look at this: [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

So finally gateway is working, but without proxy, when I add proxy line to iptables, it stop works :S, what can I do?

---

### Post by SeijiSensei on 2014-03-15
First, let's make sure the proxy is working correctly without using an iptables rule.

Configure your browser to use the proxy on port 3128.  In Firefox, use Edit > Preferences > Advanced > Network > Settings to do this.  Can you access sites that way?

Remember that squid will only proxy HTTP requests, not HTTPS.  There are methods to use squid to proxy HTTPS, but the methods are [complex]("http://wiki.squid-cache.org/Features/SslBump").

---

### Post by Exylon on 2014-03-16
> **SeijiSensei said:**
> First, let's make sure the proxy is working correctly without using an iptables rule.

Configure your browser to use the proxy on port 3128.  In Firefox, use Edit > Preferences > Advanced > Network > Settings to do this.  Can you access sites that way?

Remember that squid will only proxy HTTP requests, not HTTPS.  There are methods to use squid to proxy HTTPS, but the methods are [complex]("http://wiki.squid-cache.org/Features/SslBump").

The proxy was working with only one network card, with two don't work, so I cant access this sites :S

---

### Post by Exylon on 2014-03-20
Finally I could solve it, I made a specific guide which will help a lot of people.

---

