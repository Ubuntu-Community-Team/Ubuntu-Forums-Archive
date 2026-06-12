---
title: "apt proxy configuration gives 403 Forbidden."
date: 2014-01-16
forum: General Help
---

### Post by Gregory_Machin on 2014-01-16
Hi.

I have configured Apt-Cacher-ng to aid in conserving bandwidth and speeding up installs etc. 

I configured /etc/apt/apt.conf.d/01proxy as follows :
 Acquire::http:Proxy "http://192.168.1.1:3142/";

and I get 403 Forbidden when I run apt-get update.

I then configured /etc/apt/apt.conf.d/01proxy to use the Squid proxy
 Acquire::http:Proxy "http://192.168.1.1:3128/"
and I get 403 Forbidden when I run apt-get update.

I then configured /etc/apt/sources.list to use the proxy:
snip/
 deb [http://192.168.1.1:3142/extras.ubuntu.com/ubuntu](http://192.168.1.1:3142/extras.ubuntu.com/ubuntu) precise main
/snip
and this works without errors. 

Why would the proxy config work in /etc/apt/sources.list and not 01proxy ?

How can I get 01proxy config to work ?

Thanks






Note with out the proxy configuration updates run fine.

---

