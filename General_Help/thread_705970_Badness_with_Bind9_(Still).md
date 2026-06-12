---
title: "Badness with Bind9 (Still)"
date: 2008-02-23
forum: General Help
---

### Post by itzpapalotl on 2008-02-23
Well, I have been struggling with getting a working bind server going with Gutsy for quite a while now. I am having the old: "there is no problem, and yet it doesn't work" scenario.
What is going on on is that band is receiving the info and just denying everything.

The following is an excerpt from syslog after an /etc/init.d/bind9 restart

Feb 23 20:19:22 host0 kernel: [428176.578334] Failure registering capabilities with primary security module.
Feb 23 20:19:22 host0 named[7974]: starting BIND 9.4.1-P1 -u bind -t /var/lib/named
Feb 23 20:19:22 host0 named[7974]: found 1 CPU, using 1 worker thread
Feb 23 20:19:22 host0 named[7974]: loading configuration from '/etc/bind/named.conf'
Feb 23 20:19:22 host0 modprobe: WARNING: Not loading blacklisted module ipv6
Feb 23 20:19:22 host0 named[7974]: no IPv6 interfaces found
Feb 23 20:19:22 host0 named[7974]: listening on IPv4 interface lo, 127.0.0.1#53
Feb 23 20:19:22 host0 named[7974]: listening on IPv4 interface eth0, 216.110.197.32#53
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 254.169.IN-ADDR.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 2.0.192.IN-ADDR.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 255.255.255.255.IN-ADDR.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 1.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.0.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: D.F.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 8.E.F.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: 9.E.F.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: A.E.F.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: automatic empty zone: B.E.F.IP6.ARPA
Feb 23 20:19:22 host0 named[7974]: command channel listening on 127.0.0.1#953
Feb 23 20:19:22 host0 named[7974]: zone 0.in-addr.arpa/IN: loaded serial 1
Feb 23 20:19:22 host0 named[7974]: zone 127.in-addr.arpa/IN: loaded serial 1
Feb 23 20:19:22 host0 named[7974]: zone 255.in-addr.arpa/IN: loaded serial 1
Feb 23 20:19:22 host0 named[7974]: zone localhost/IN: loaded serial 1
Feb 23 20:19:22 host0 named[7974]: running
Feb 23 20:19:47 host0 named[7974]: client 217.199.161.224#45959: query (cache) '91.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:20:02 host0 named[7974]: client 200.42.213.11#33882: query (cache) '24.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:20:20 host0 named[7974]: client 193.95.161.222#53: query (cache) '24.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:20:28 host0 named[7974]: client 69.228.144.138#1065: query (cache) 'www.google.com/A/IN' denied
Feb 23 20:20:28 host0 named[7974]: client 69.228.144.138#1065: query (cache) 'www.google.com.gateway.2wire.net/A/IN' denied
Feb 23 20:21:43 host0 named[7974]: client 69.16.234.73#2775: query (cache) '171.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:21:48 host0 named[7974]: client 69.228.144.138#1065: query (cache) 'ubuntu.forums.org/A/IN' denied
Feb 23 20:21:48 host0 named[7974]: client 69.228.144.138#1065: query (cache) 'ubuntu.forums.org.gateway.2wire.net/A/IN' denied
Feb 23 20:22:20 host0 named[7974]: client 205.208.227.32#32768: query (cache) '121.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:22:22 host0 named[7974]: client 208.252.125.83#43601: query (cache) '237.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:22:31 host0 named[7974]: client 206.63.33.80#32768: query (cache) '248.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:22:40 host0 named[7974]: client 80.50.50.21#35880: query (cache) '24.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:22:42 host0 named[7974]: client 88.112.210.245#46800: query (cache) '24.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:22:52 host0 named[7974]: client 209.50.225.40#11279: query (cache) '198.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:23:54 host0 named[7974]: client 208.67.217.4#30489: query (cache) '202.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:26:36 host0 named[7974]: client 216.98.128.157#25368: query (cache) '243.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:27:16 host0 named[7974]: client 81.29.198.131#32774: query (cache) '81.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:27:23 host0 named[7974]: client 12.120.125.57#52614: query (cache) '81.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:27:40 host0 named[7974]: client 150.176.12.51#34225: query (cache) '152.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:28:34 host0 named[7974]: client 205.208.227.33#33210: query (cache) '121.217.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:29:09 host0 modprobe: WARNING: Not loading blacklisted module ipv6
Feb 23 20:29:25 host0 named[7974]: client 216.98.128.157#17743: query (cache) '217.197.110.216.in-addr.arpa/PTR/IN' denied
Feb 23 20:29:32 host0 modprobe: WARNING: Not loading blacklisted module ipv6

any ideas?

---

### Post by CarbonToast on 2008-05-07
I just ran into this issue as well on an upgrade, here is a good description on what has happened and how to make it work like it did before:

[http://www.isc.org/index.pl?/sw/bind/docs/support_bulletin_200707.php]("http://www.isc.org/index.pl?/sw/bind/docs/support_bulletin_200707.php")

---

