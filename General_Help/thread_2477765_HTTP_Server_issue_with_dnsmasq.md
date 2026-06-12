---
title: "HTTP Server issue with dnsmasq"
date: 2022-08-06
forum: General Help
---

### Post by wcnackers on 2022-08-06
HI, 

Am trying to setup an HTTP boot Server and the instructions I have state to create an /etc/hosts.conf file that contains the following assignments:
[I]
192.168.111.1 [www.httpboot.local]("http://www.httpboot.local")
2001:db8:f00f:cafe::1 [www.httpboot.local]("http://www.httpboot.local")

[/I]In the /etc/dnsmasq.conf file I hvae addn-hosts=/etc/hosts.conf.   When I execute "sudo systemctl start dnsmasq", the system returns a prompt with no error.  But when I look at "sudo systemctl status dnsmasq" it states:  [B]"failed to load names from /etc/hosts.conf:  permission denied"

[/B]I have tried to change owners, change mode, move the file to different directories...nothing.   Does anyone have any idea why this happening and if there is a fix or a workaround.  "eth1" is configured with the ip addresses from above and [www.httpboot.local]("http://www.httpboot.local") is listed in the grub.cfg file for the ipv4 and ipv6 menu entries.

I would appreciate any feedback if anyone has any inkling of what I am doing wrong or what I can do to resolve the problem.

Thanks in advance,

wcnackers

---

### Post by TheFu on 2022-08-06
```
 "failed to load names from /etc/hosts.conf: permission denied"
```

So, what is the output from ls -al  /etc/hosts.conf?  We shouldn't need to ask. There is something you've missed. More eyes will likely see it.

BTW, I think it is a terrible idea to use .local. That is what Avahi and other mDNS tools use, so there could be conflicts.  Rather, make up another TLD - say .lan.  I use .foo.  These need to be names that don't resolve anywhere on the internet.

---

### Post by ActionParsnip on 2022-08-07
[https://community.ui.com/questions/Why-does-host-file-have-empty-permissions-re-dnsmasq-and-permission-denied-reading-etc-hosts/c0c280bd-9d23-40f5-8661-79d089f151ee](https://community.ui.com/questions/Why-does-host-file-have-empty-permissions-re-dnsmasq-and-permission-denied-reading-etc-hosts/c0c280bd-9d23-40f5-8661-79d089f151ee)

Check permissions. Should be 0644

---

### Post by wcnackers on 2022-08-07
Sorry you had to ask.

Contents of hosts.conf:
[I]  192.168.1.111.1 [www.httpboot.local](www.httpboot.local)
  2001:db8:f00f:cafe::1 [www.httpboot.local](www.httpboot.local)
[/I]
As for using .local instead of .lan or .foo, I am simply following instructions that were given to me and it said.local  The server is not on a "live network".  It is just this server hooked to a switch and another computer hooked to the switch booting from this server.  It's simply to test that the client can boot from the http boot server.  Right now the client starts to boot, gets an ip address and then stops.

---

### Post by wcnackers on 2022-08-07
I did check permissions.  They are correct.  I also tried just opening all permissions up and used 0777.  Nothing works.

---

### Post by wcnackers on 2022-08-07
ls -al /etc/hosts.conf
-rw-r--rw-- 1 test root 74 Aug 6 09:45 /etc/hosts.conf

---

### Post by TheFu on 2022-08-07
[code=wcnackers;14107134]ls -al /etc/hosts.conf
-rw-r--rw-- 1 test root 74 Aug 6 09:45 /etc/hosts.conf[/code]

This is wrong.
It needs to be 
644 root:root
as in:
```
$ ll /etc/hosts
-rw-r--r-- 1 root root 458 Oct 25  2020 /etc/hosts
```

/hosts.conf is something else, completely.  

I use dnsmasq for a simple LAN DNS.  The name of the local file that I use is lan.list.  It is located inside /etc/pihole/lan.list
The dnsmasq config for it is in /etc/dnsmasq.d/02-lan.conf which has 1 line:
```
addn-hosts=/etc/pihole/lan.list
```

The contents of that file looks like a /etc/hosts file, except there must be at least 2 host entries per IP address.  My testing shows that the order of those entries matters:
```
# {IP}     {hostname}     {hostname}.{domainname}
172.22.22.3     regulus     regulus.foo.lan

```
is an example.  Permissions, owner and group are:
```
$ ll lan.list 
-rw-r--r-- 1 root root 5185 Dec 20  2021 lan.list
```

---

### Post by wcnackers on 2022-08-07
Thanks for your help.  I will try to see if i can fix it.

---

### Post by wcnackers on 2022-08-10
Tried all suggestions.  Still can't get it to work.  I was able to work around the problem by just substituting the actual IP address for the URL.  It's just a test server so I'm not really worried about bypassing DNS...it just really bothers me.   Anyway, thanks for all input and suggestions.   Greatly appreciated.   

wcnackers

---

### Post by TheFu on 2022-08-10
> **wcnackers said:**
> Sorry you had to ask.

Contents of hosts.conf:
[I]  192.168.1.111.1 [www.httpboot.local](www.httpboot.local)
  2001:db8:f00f:cafe::1 [www.httpboot.local](www.httpboot.local)
[/I]
As for using .local instead of .lan or .foo, I am simply following instructions that were given to me and it said.local  The server is not on a "live network".  It is just this server hooked to a switch and another computer hooked to the switch booting from this server.  It's simply to test that the client can boot from the http boot server.  Right now the client starts to boot, gets an ip address and then stops.

Having 2 computers on a switch, with not routing doesn't work, unless that switch has L2 routing. Some enterprise switches can do this, but I double any switch under $500 can.  The solution is to setup routing from A-->B and from B-->A manually in each computer's routing table.  I'm a little surprised that using an IP address will work.

Again, /etc/hosts.conf doesn't do what you want. It is a config file for something completely different left over from the early 1990s.  I haven't seen one used since then, with nsswitch.conf took over. [https://tldp.org/LDP/nag/node82.html](https://tldp.org/LDP/nag/node82.html) explains the purpose ... but nsswitch.conf is where this stuff has been handled for decades.

---

### Post by wcnackers on 2022-08-17
Sorry I didn't answer you sooner.  Life detour.  

I thought putting a "DHCP server" on a switch with another computer would work kind of like using a crossover cable between the two, like an old peer-to-peer.  I haven't had a chance to look in the nsswitch stuff yet but I will.   

To be honest, all of this is on OpenSUSE.  Sorry.  I have been switching back and forth between OS's trying to get something to work and I forgot what OS and what instructions I was on when I posted my original question.  

I've closed the thread but thanks for latest reply.

---

