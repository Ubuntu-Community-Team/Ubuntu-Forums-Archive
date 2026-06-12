---
title: "Can't  ping on Ubuntu 18.04"
date: 2018-06-09
forum: General Help
---

### Post by bizhat on 2018-06-09
On Ubuntu 18.04, i can't ping from terminal

```
boby@ok-pc-01:~$ ping google.com
connect: Network is unreachable
boby@ok-pc-01:~$ 

```


My resolv.conf have this

```
boby@ok-pc-01:~$ cat /etc/resolv.conf 
# This file is managed by man:systemd-resolved(8). Do not edit.
#
# This is a dynamic resolv.conf file for connecting local clients to the
# internal DNS stub resolver of systemd-resolved. This file lists all
# configured search domains.
#
# Run "systemd-resolve --status" to see details about the uplink DNS servers
# currently in use.
#
# Third party programs must not access this file directly, but only through the
# symlink at /etc/resolv.conf. To manage man:resolv.conf(5) in a different way,
# replace this symlink by a static file or a different symlink.
#
# See man:systemd-resolved.service(8) for details about the supported modes of
# operation for /etc/resolv.conf.

nameserver 127.0.0.53
search Home
boby@ok-pc-01:~$ 

```


When i do nslookup, it fails


```
boby@ok-pc-01:~$ nslookup google.com 127.0.0.53
Server:		127.0.0.53
Address:	127.0.0.53#53

** server can't find google.com: SERVFAIL

boby@ok-pc-01:~$ 

```

systemd-resolve --status  shows following result


```

boby@ok-pc-01:~$ systemd-resolve --status
Global
          DNS Domain: Home
          DNSSEC NTA: 10.in-addr.arpa
                      16.172.in-addr.arpa
                      168.192.in-addr.arpa
                      17.172.in-addr.arpa
                      18.172.in-addr.arpa
                      19.172.in-addr.arpa
                      20.172.in-addr.arpa
                      21.172.in-addr.arpa
                      22.172.in-addr.arpa
                      23.172.in-addr.arpa
                      24.172.in-addr.arpa
                      25.172.in-addr.arpa
                      26.172.in-addr.arpa
                      27.172.in-addr.arpa
                      28.172.in-addr.arpa
                      29.172.in-addr.arpa
                      30.172.in-addr.arpa
                      31.172.in-addr.arpa
                      corp
                      d.f.ip6.arpa
                      home
                      internal
                      intranet
                      lan
                      local
                      private
                      test

Link 3 (wlxe8de270b3955)
      Current Scopes: DNS
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
         DNS Servers: 192.168.1.1
          DNS Domain: Home

Link 2 (enp7s1)
      Current Scopes: none
       LLMNR setting: yes
MulticastDNS setting: no
      DNSSEC setting: no
    DNSSEC supported: no
boby@ok-pc-01:~$ 

```

If i nslookup with 192.168.1.1, it works, this is my router

```

boby@ok-pc-01:~$ nslookup google.com 192.168.1.1
Server:		192.168.1.1
Address:	192.168.1.1#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.163.78
Name:	google.com
Address: 2404:6800:4007:80c::200e

boby@ok-pc-01:~$ 

```

What is the proper way to fix the ping ? I can manually edit resolv.conf, but it get over written on boot. 

Somehow this problem is only with terminal, my browsers can browse web sites properly.

---

### Post by bizhat on 2018-06-09
I got it fixed. The problem was with /etc/hosts, i moved this file to my home directory for easy editing and created a symlink. For some reason resolve fail when it is a symlink. This used to work with Ubuntu 16.04

---

