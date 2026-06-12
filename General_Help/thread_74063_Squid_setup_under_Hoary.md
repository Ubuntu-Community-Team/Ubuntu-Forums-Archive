---
title: "Squid setup under Hoary"
date: 2005-10-10
forum: General Help
---

### Post by Dagr on 2005-10-10
Hello, I recently installed Hoary on my old pc (Athlon 1.4, 512MB, etc...) as I found Ubuntu to be incredibly easy to use.

I am slowly building this pc into a server, and secondary desktop.
At the request of a friend I am trying to setup squid to authenticate against samba.

I installed the webmin package as suggested by another Squid help thread.

My problem is that Squid will not start, complaining of incomplete authentication setup. 

It seems that all of the authentication programs are already compiled and available.

Samba seems to be working fine (I access the machine from my primary desktop constantly) I have the users and samba passwords setup. I do not know what else to do. I have been searching in vain for two weeks for a solution to my problem. I am including my /etc/squid/squid.conf below, hopefully someone can help. Thanks.
```

acl manager proto cache_object
acl localhost src 127.0.0.1/255.255.255.255
acl to_localhost dst 127.0.0.1/255.255.255.255
acl SSL_ports port 443 563  	#https, snews
acl SSL_ports port 873 		#rsync
acl Safe_ports port 80 		#http
acl Safe_ports port 21		#ftp
acl Safe_ports port 443 563 	#https, snews
acl Safe_ports port 70		#gopher
acl Safe_ports port 210		#wais
acl Safe_ports port 1025-65535	#unregistered
acl Safe_ports port 280 	#http-mgmt
acl Safe_ports port 488		#gss-http
acl Safe_ports port 591		#filemaker
acl Safe_ports port 777		#multiling
acl Safe_ports port 631		#cups
acl Safe_ports port 873		#rsync
acl Safe_ports port 901		#SWAT
acl all src 0/0


#acl Dave proxy_auth REQUIRED
acl Dave proxy_auth
#auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/squid_passwd
#auth_param basic children 2

auth_param basic program /usr/lib/squid/ntla_auth
auth_param basic children 2

http_port 3128
no_cache deny all
cache_dir null /tmp

ftp_passive off
hosts_file /etc/hosts
refresh_pattern ^ftp:		1440	20%	10080
refresh_pattern ^gopher:	1440	0%	1440
refresh_pattern .		0	20%	4320
negative_dns_ttl 0

http_access allow Dave
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny to_localhost
http_access deny all

snmp_port 0
snmp_access deny all
prefer_direct on
detect_broken_pconn on

cache_effective_user ian
cache_effective_group ian


```

Thanks for any help!
  ~  Dagr

EDIT: if anyone can tell me how to administer squid and apache withOUT webmin, I'd be most grateful. I dislike webmin, but don't know how to start/stop/etc apache and squid without it...

---

