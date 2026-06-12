---
title: "squid, edubuntu, and other . . . stuff"
date: 2007-02-19
forum: General Help
---

### Post by Anivair on 2007-02-19
I just set up our new ltsp environment using the default edubuntu install.  So far so good.  I recommend it. 

However, I can't get squid to work at all.  On our old machine it ran just fine, but here, even if I use the same squid.conf file, it's just not running. 

Hopefully someone can take a look here and see what's up. 

I'm running the most recent edubuntu. 
I'm running squid version 2.6

Here's m y old squid.conf.  I've taken out the comments for ease of seeing, but I have also liked to it with full comments below, for those of you who want comments.  

```
 http_port 3128
 icp_port 3130
 htcp_port 0
hierarchy_stoplist cgi-bin ?
acl QUERY urlpath_regex cgi-bin \?
no_cache deny QUERY
 cache_mem 8 MB
 maximum_object_size 20 MB
 cache_dir ufs /var/spool/squid 10000 16 256
 cache_access_log /var/log/squid/access.log
 cache_log /var/log/squid/cache.log
 pid_filename /var/run/squid.pid
hosts_file /etc/hosts
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	10080
acl all src 0.0.0.0/0.0.0.0
acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.0/8
acl local-lan0 src 100.100.100.2/255.255.255.0
acl local-lan1 src 100.100.100.113/255.255.255.0
acl local-lan2 src 100.100.100.114
acl allowedurls dstdomain .whitepages.com .yellowpages.com 100.100.100.10 rossman-central .gov 100.100.100.3 server
acl SSL_ports port 443 563	# https, snews
acl SSL_ports port 873		# rsync
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443 563	# https, snews
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
acl Safe_ports port 631		# cups
acl Safe_ports port 873		# rsync
acl Safe_ports port 901		# SWAT
acl purge method PURGE
acl CONNECT method CONNECT
 http_access allow local-lan0 local-lan1 local-lan2
 http_access allow allowedurls
 http_access deny !allowedurls
http_access allow manager localhost
http_access deny manager
http_access allow purge localhost
http_access deny purge
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access allow localhost
http_access deny all
http_reply_access allow all
icp_access allow all
  cache_peer 100.100.100.254 parent 3128 3130 default no-query
visible_hostname ltsp-1
 memory_pools off
coredump_dir /var/spool/squid
```

[http://www.anivair.com/downloads/squid.conf]("http://www.anivair.com/downloads/squid.conf")

When I run this squid.conf I get the following (I suspect common) error in firefox: 

```
The Proxy Server is refusing connections. 

Firefox is configured to use a proxy server, but that is refusing connections.  
```

When I restart squid, I get this, which looks like it's actually ok, despite the warnings: 

```
rossman@ltsp-1:~$ sudo /etc/init.d/squid restart
Password:
 * Restarting Squid HTTP proxy squid                                            
2007/02/19 13:49:34| aclParseIpData: WARNING: Netmask masks away part of the specified IP in '100.100.100.2/255.255.255.0'
2007/02/19 13:49:34| aclParseIpData: WARNING: Netmask masks away part of the specified IP in '100.100.100.113/255.255.255.0'
                                                                           [ ok ]

```

I'm at a loss. 

Anyone?

---

