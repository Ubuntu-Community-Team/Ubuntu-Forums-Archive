---
title: "DNS Server Woes"
date: 2007-05-28
forum: General Help
---

### Post by xelapond on 2007-05-28
I just tried to set up a DNS server with the guide from "Ubuntu Hacks".  I configured all my files and when i did an nslookup on the domain name i get this:

alex@Shuttle-Linux:~$ nslookup [www.**********.net](www.**********.net)
Server:         192.168.2.1
Address:        192.168.2.1#53

** server can't find [www.**********.net:](www.**********.net:) NXDOMAIN

Then when I try my mail domain:

alex@Shuttle-Linux:~$ nslookup mail.**********.net
Server:         192.168.2.1
Address:        192.168.2.1#53

** server can't find mail.**********.net: NXDOMAIN


here is my zone file:

**********.net. IN	SOA	ns1.**********.net. me.**********.net. (
	2001061407  ;  serial
	10800       ; refresh
	3600        ; retry
	432000      ; expire
	38400 )     ; ttl
**********.net. IN	NS	ns1.**********.net.
**********.net. IN	NS	ns2.**********.net.
**********.net. IN	MX	30 mail.**********.net.
[www.**********.net](www.**********.net).	IN	A     localhost
mail.**********.net.	IN	A	localhost


Any ideas as to why it is doing this and what I can do to fix it.  I am trying to run a webserver(apache, php), mailserver(postfix), ssh prompt(openssh-server)  on one machine.  Is this my problem?

Thanks, Alex

---

