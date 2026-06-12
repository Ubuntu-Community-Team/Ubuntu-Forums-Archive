---
title: "squid ssl bump problem"
date: 2017-09-13
forum: General Help
---

### Post by aminbaik on 2017-09-13
Hello,
I tried to instll squid using this steps:
[https://www.howtoforge.com/filtering-https-traffic-with-squid](https://www.howtoforge.com/filtering-https-traffic-with-squid) without installing Diladele Web Safety
when I try to using ssl bump option the squid is refusing connection but when i don't use it it's work fine so where is the problem ?
```

acl localnet src 192.168.168.0/24
acl localnet src 192.168.4.0/24
acl SSL_ports port 443
acl Safe_ports port 80		# http
acl Safe_ports port 21		# ftp
acl Safe_ports port 443		# https
acl Safe_ports port 70		# gopher
acl Safe_ports port 210		# wais
acl Safe_ports port 1025-65535	# unregistered ports
acl Safe_ports port 280		# http-mgmt
acl Safe_ports port 488		# gss-http
acl Safe_ports port 591		# filemaker
acl Safe_ports port 777		# multiling http
#acl CONNECT method CONNECT
http_access allow Safe_ports
http_access allow localhost manager
http_access allow localhost
http_access allow localnet
#http_port 3128 
http_port 3128 ssl-bump cert=/etc/squid3/ssl_cert/myCA.pem
always_direct allow all
ssl_bump allow all
#sslproxy_cert_error allow all
#sslproxy_flags DONT_VERIFY_PEER
#sslcrtd_program /usr/lib/squid3/ssl_crtd -s /var/lib/ssl_db -M 4MB
#sslcrtd_children 5

 forwarded_for off
  request_header_access Allow allow all
  request_header_access Authorization allow all
  request_header_access WWW-Authenticate allow all
  request_header_access Proxy-Authorization allow all
  request_header_access Proxy-Authenticate allow all
  request_header_access Cache-Control allow all
  request_header_access Content-Encoding allow all
  request_header_access Content-Length allow all
  request_header_access Content-Type allow all
  request_header_access Date allow all
  request_header_access Expires allow all
  request_header_access Host allow all
  request_header_access If-Modified-Since allow all
  request_header_access Last-Modified allow all
  request_header_access Location allow all
  request_header_access Pragma allow all
  request_header_access Accept allow all
  request_header_access Accept-Charset allow all
  request_header_access Accept-Encoding allow all
  request_header_access Accept-Language allow all
  request_header_access Content-Language allow all
  request_header_access Mime-Version allow all
  request_header_access Retry-After allow all
  request_header_access Title allow all
  request_header_access Connection allow all
  request_header_access Proxy-Connection allow all
  request_header_access User-Agent allow all
  request_header_access Cookie allow all
  request_header_access All deny all


```

so where is the problem ?
thanks.

---

