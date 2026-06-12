---
title: "weird DNS problems ?"
date: 2006-10-14
forum: General Help
---

### Post by GoBieN on 2006-10-14
I'm having a very strange problem on my Dapper server. It's a LAMP + samba + ssh + ftp + xvnc  server.

Now for the problem, i wanted to install automatix, for some easy installing of a few stuff i had in mind. Automatix would not install because of error importing some keyes. Thats how i found. Check this out:
```
stan@ARES:~$ nslookup www.getautomatix.com
Server:         192.168.1.254
Address:        192.168.1.254#53

Non-authoritative answer:
Name:   www.getautomatix.com
**Address: 82.165.194.143**

stan@ARES:~$ wget www.getautomatix.com
--11:41:04--  http://www.getautomatix.com/
           => `index.html'
**Resolving www.getautomatix.com... 84.195.63.135**
Connecting to www.getautomatix.com[84.195.63.135]:80...
```
The automatix site is just an example, i have this with about half the internet. For example this site:
```
stan@ARES:~$ nslookup www.ubuntuforums.org
Server:         192.168.1.254
Address:        192.168.1.254#53

Non-authoritative answer:
Name:   www.ubuntuforums.org
Address: 82.211.81.186

stan@ARES:~$ wget www.ubuntuforums.org
--11:48:35--  http://www.ubuntuforums.org/
           => `index.html'
Resolving www.ubuntuforums.org... 69.25.27.170

```
My hosts file seems in order:
```
stan@ARES:~$ cat /etc/hosts
127.0.0.1 localhost
192.168.1.1 ARES.telenet.be ARES
192.168.1.130 laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
My NIC:
```
stan@ARES:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:E0:18:59:9F:0B
          inet addr:192.168.1.1  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:18ff:fe59:9f0b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27865 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:3219550 (3.0 MiB)  TX bytes:42143368 (40.1 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172695 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172695 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:364433034 (347.5 MiB)  TX bytes:364433034 (347.5 MiB)

stan@ARES:~$                                                           
```

Help me please ?

---

### Post by GoBieN on 2006-10-14
And when i try to surf to such a site. like for example [www.ubuntuforums.org](www.ubuntuforums.org) then i got a page saying.
> ops. There may be an issue with the URL Forwarding service for this
domain, in which case our technical staff is currently working the situation. Otherwise, this domain is currently under construction and will be back online soon.
Screenshot: [http://www.xpiria.be/images/dns-trouble.png](http://www.xpiria.be/images/dns-trouble.png)

Help would be appreciated ;)

---

### Post by dentaku65 on 2006-10-14
Try to put in /etc/hosts only this entry:

```
127.0.0.1 localhost
```

And comment out with # all the others; then change your isp dns in /etc/resolv.conf with others (here are the mine):
62.211.69.150
212.48.4.15

If you use dhcp (I don't think because you set up a server) you can ad the dns directly into the /etc/dhcp3/dhclient.conf
reach these lines:
```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;

```
and add the dns as next line:
```
supersede domain-name-servers 62.211.69.150;
prepend domain-name-servers 212.48.4.15;

```

Hope this help.

---

### Post by GoBieN on 2006-10-15
Hey,

I do use DHCP but have set a static DNS entry for the MAC address of my server in my NAT router.

So the router is playing caching DNS server, and sends his own IP as DNS server trough DHCP. I now changed the IP adress in resolv.conf to a DNS server from my ISP 195.130.130.5 I can use only those, since my ISP blocks DNS requests to outside the network. But it did not help.

/etc/resolv.conf```
search gobien.be
nameserver 192.168.1.254
```
Changed to:```
search gobien.be
nameserver 195.130.130.5
```
I also commented out all thos ipv6 lines in the hosts file.
Stillt the same problem:
> stan@ARES:~$ nslookup [www.ubuntuforums.org](www.ubuntuforums.org)
Server:         195.130.130.5
Address:        195.130.130.5#53

Non-authoritative answer:
Name:   [www.ubuntuforums.org](www.ubuntuforums.org)
Address: 82.211.81.186

stan@ARES:~$ wget [www.ubuntuforums.org](www.ubuntuforums.org)
--20:57:07--  [http://www.ubuntuforums.org/](http://www.ubuntuforums.org/)
           => `index.html'
Resolving [www.ubuntuforums.org](www.ubuntuforums.org)... 66.150.161.141
Connecting to [www.ubuntuforums.org](www.ubuntuforums.org)[66.150.161.141]:80... connected.


---

### Post by GoBieN on 2006-10-21
```
stan@ARES:~$ echo $http_proxy

stan@ARES:~$
``` No http proxy

```

stan@ARES:~$ ps ax | grep named
31770 ?        Ssl    0:00 /usr/sbin/named -u bind -t /var/lib/named
10935 ?        SNs    0:00 /sbin/syslogd -u syslog -a /var/lib/named/dev/log
17767 pts/0    R+     0:00 grep named
stan@ARES:~$
```

But i do have a named server running it seems.


Anyone pls ?

---

### Post by lloyd_b on 2006-10-21
I tried your examples from the original post, and got the same results.  The first time.  Every time after that nslookup and wget matched.

Could this simply be some sort of DNS cacheing issue?  

Lloyd B.

---

### Post by GoBieN on 2006-10-21
Well i seem to have solved the issue.

I took a deeper look at those IP adresses i always got, the 64.x.x.x and 66.x.x.x and so on 

After some reverse DNS lookups i realized that those IP adresses were all adresses that belong to the company that handels my DNS for my domain i have on the internet.

I set my local router (NAT) to DHCP server and set a domain called gobien.be in the options there. I also installed samba, and set it as domainmaster to gobien.be.

Now appearently there was some kind of mixup between my locally used domain name gobien.be and the one i have on the internet (also gobien.be). So it would seem that DNS requests for browsing the internet and using wget were send to the Nameserver of my public domain gobien.be instead of the local cached DNS server from ym router or the ISP's DNS server.

I now removed the domain option from my DHCP server, and i removed the line "search gobien.be" from /etc/recolv.conf" i restarted the BIND9 (named) server, rebooted the DHCP router and renewed my DHCP on the server.

Guess what problem solved !

---

