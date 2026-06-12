---
title: "Squid"
date: 2015-01-23
forum: General Help
---

### Post by chris240 on 2015-01-23
Hi,

I am having problem with squid3 when i access Google search doesn't work and Bing or other site works. What i did ass well is a nslookup on Google i use the IP address then it works. I did double check DNS weird enough BING search or Yahoo search engine works fine, except Google search engine and lot of our people use Google search engine. and it just load the hole time when access Google Search engine.
Here is my squid file.

acl manager proto cache_object
acl localhost src 127.0.0.1/32 ::1
acl to_localhost dst 127.0.0.0/8 0.0.0.0/32 ::1
acl SSL_ports port 443
acl Safe_ports port 80 # http
acl Safe_ports port 21 # ftp
acl Safe_ports port 443 # https
acl Safe_ports port 70 # gopher
acl Safe_ports port 210 # wais
acl Safe_ports port 1025-65535 # unregistered ports
acl Safe_ports port 280 # http-mgmt
acl Safe_ports port 488 # gss-http
acl Safe_ports port 591 # filemaker
acl Safe_ports port 777 # multiling http
acl CONNECT method CONNECT
acl SSL_ports port 20000 10000
acl purge method
acl all src
acl password proxy_auth REQUIRED
acl localnet src 192.168.127.0/255.255.248.0
http_access deny manager
http_access allow localhost purge
http_access deny purge
http_access allow SSL_ports Safe_ports
http_access allow password
http_access allow localhost
http_access allow localnet
http_access deny all
http_port 3128
coredump_dir /var/spool/squid3
refresh_pattern ^ftp:           1440    20%     10080
refresh_pattern ^gopher:        1440    0%      1440
refresh_pattern -i (/cgi-bin/|\?) 0     0%      0
refresh_pattern (Release|Packages(.gz)*)$      0       20%     2880
refresh_pattern .               0       20%     4320
cache_effective_user proxy
visible_hostname #############
dns_nameservers 196.41.124.10 196.41.124.11
hosts_file /etc/hosts
cache_effective_group proxy
dns_nameservers 196.41.124.10 196.41.124.11

---

### Post by SeijiSensei on 2015-01-23
Remember that Squid uses the local DNS on its machine when it needs to resolve names.  If you open a browser on the Squid server (use elinks if you don't have a GUI) and access Google, does it work properly?

Also Google defaults to HTTPS these days which Squid cannot proxy without a [lot](http://wiki.squid-cache.org/Features/SslBump) of extra configuration.  You're not trying to send HTTPS requests to port 3128 are you?  In a standard configuration, Squid should be used for HTTP connections on port 80, and all port 443 connections should go directly to the Internet and not through the proxy.

---

### Post by chris240 on 2015-01-26
thanx for the reply. We use HTTPS requests on port 3128 like google

---

### Post by SeijiSensei on 2015-01-26
Won't work unless you activate SSLBump and distribute the appropriate certificates to all the clients.  Did you read the page I linked to above?

---

