---
title: "COnfiguring Squid3 to allow passthru of web traffic to local devices"
date: 2014-09-06
forum: General Help
---

### Post by William_Parks_Walk on 2014-09-06
I just installed Ubuntu Desktop 32 bit edition. I also installed the latest squid3 package. I configured my static ip address and pointed my device to the squid3 proxy server machine and then used sudo tail -f /var/log/squid3/access.log to watch the access log live while my connected device attempts to get data cached on the Squid server. I switched my http_port to 8888 based on one websites recommendation. Here are some error messages I am getting from my access.log  

1410048951.507  0 192.168.1.51 TCP_DENIED/403 3577 CONNECT graph.facebook.com:443 - HEIR_NONE/- text/html

1410048952.390  0 192.168.1.51 TCP_DENIED/403 3618 CONNECT api.tapstream.com:443 - HIER_NONE/- text/html  

I have tried to mess with the /eetc/squid3/squid3.conf file but to no avail. I even tried to disable the firewall - ufw  disable. Still no luck. Help! Also is there a way to store and load the files Im trying to cache on the hard drive so when the service starts back up I can take off where I left off. I need to move the server back and forth from my 2 offices as travel requires.

---

### Post by SeijiSensei on 2014-09-07
Don't try pushing HTTPS traffic through Squid unless you're willing to install and configure [SSLBump]("http://wiki.squid-cache.org/Features/SslBump").  Use Squid for HTTP and send HTTPS requests directly to the servers.

All the cached files are stored locally on the machine in /var/spool/squid3.  They will go anywhere the server does.  Squid reads its cache upon startup.

---

### Post by William_Parks_Walk on 2014-09-07
I dont mind installing and configuring ssl bump but I find myself in a dilemma. I've got Squid3 installed and I have been able to debug why it is not working but I don't understand why I need to install anything else. All I want Squid to do is cache web files for saving on my bandwidth traffic. I am not looking for security. I have Ubuntu installed on a VM and all I want to do with it is use it as a local cache proxy only. It is all behind a hardware firewall (router). Cant I just disable any security protocols withing Ubuntu / Squid? This is only going to be used for me. I don't care if I have to tell my phone that the connection is not secure.

---

### Post by SeijiSensei on 2014-09-08
Most people overestimate how much caching Squid will do.  Mostly it will consist of repeatedly used graphics like icons and such.  Many web pages are dynamically generated and not cache-able.  Things like videos are often distributed with the "no-caching" headers set to discourage copyright infringement.

I maintain a Squid cache in front of 200+ users.  The entire cache occupies just 9 GB.  Most of the entries are less than 10K.

Your browser already does caching for you.  If you're the only user, adding Squid won't help much.

---

