---
title: "get web stat from socks5 host"
date: 2016-03-07
forum: General Help
---

### Post by marchello_lippi2 on 2016-03-07
Hi all, 

I got vps that I use as ssh socks5 proxy. No additional software as squid etc is used. My need is to know what sites were visited and what bandwidth was spent for each of them. 

How do I get stat from this remote host? I got root access to that host. 

Thanks ahead.

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:        14.04
Codename:       trusty

---

### Post by SeijiSensei on 2016-03-07
You could log all connections with iptables rules.  For instance
```
sudo /sbin/iptables -I INPUT -p tcp -s your_network --dport 80 -j LOG
```
replacing "your_network" with an IP subnet like 192.168.1.0/24.  That will write an entry to syslog for every outbound connection to port 80.  You won't see the URLs, though, just the destination IPs.  If you really want to track usage, I recommend using a transparent Squid proxy instead.

---

### Post by marchello_lippi2 on 2016-03-07
[[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000],

What subnet should be for [/COLOR]127.0.0.1/255.0.0.0 and for 127.0.0.2/255.255.255.255 ? 
I'm sorry, I'm not good in networking.

---

### Post by SeijiSensei on 2016-03-07
Why do you care about those?  Those are the addresses assigned to the "localhost" interface on the machine itself.  If you're trying to log connections, aren't you more concerned about ones coming into the server via the proxy?

That said, you can just modify the command I gave like this:
```
sudo /sbin/iptables -I INPUT -p tcp -s 127.0.0.0/8 --dport 80 -LOG
sudo /sbin/iptables -I INPUT -p tcp -s your_network --dport 80 -j LOG
```

This won't help much with bandwidth usage though.  If that's really important, I'd look into something like [ntop](http://www.ntop.org/).  It's in the Ubuntu repositories.  That will run a nice little web-based application that will tell you more than you ever need to know about the server's traffic.  If you go the ntop route, you won't need any iptables rules.

---

### Post by marchello_lippi2 on 2016-03-07
[[COLOR=#000000]SeijiSensei[/COLOR]]("http://ubuntuforums.org/member.php?u=698195")[COLOR=#000000][COLOR=#000000],

thanks.[/COLOR][/COLOR]

---

