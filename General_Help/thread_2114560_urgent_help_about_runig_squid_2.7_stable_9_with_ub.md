---
title: "urgent help about runig squid 2.7 stable 9 with ubunt 12.10"
date: 2013-02-10
forum: General Help
---

### Post by drvirus on 2013-02-10
hi ,
i have server Delr720 and i want to use it as a squid cache server .
i installled ubuntu 12.10 64 bit server edititon .
i want to compile squid 2.7 stable and i must be enabling  " tproxy mode " so that clients will go  internet with thier original ips .
i followed the steps below :
================
 # sudo apt-get update
   # sudo apt-get install gcc
  # sudo apt-get install build-essential
  # sudo apt-get install sharutils
  # sudo apt-get install ccze
  # sudo apt-get install libzip-dev
  # sudo apt-get install automake1.9
  
  # wget [http://horvet.googlecode.com/files/squid-2.7.STABLE-9%2Bpatch.tar.gz]("http://horvet.googlecode.com/files/squid-2.7.STABLE-9%2Bpatch.tar.gz")
  # tar xvf squid-2.7.STABLE-9+patch.tar.gz
  # cd squid-2.7.STABLE9

./configure --prefix=/usr --exec_prefix=/usr --bindir=/usr/sbin  --sbindir=/usr/sbin --libexecdir=/usr/lib/squid --sysconfdir=/etc/squid \
 --localstatedir=/var/spool/squid  --datadir=/usr/share/squid --enable-http-gzip --enable-async-io=24  --with-aufs-threads=24 --with-pthreads --enable-storeio=aufs \
 --enable-linux-netfilter --enable-arp-acl --enable-epoll --enable-removal-policies=heap --with-aio --with-dl --enable-snmp \
 --enable-delay-pools --enable-htcp --enable-cache-digests --disable-unlinkd --enable-large-cache-files --with-large-files \
 --enable-err-languages=English --enable-default-err-language=English --with-maxfd=65536



#make
# sudo make install


after the steps above , when i type /etc/init.d/squid  is not found
i mean that i cant type /etc/init.d/squid/start or stop

my question is , am i missing some libraries ?
why i cant find squid in /etc/init.d/squid

do i need any other steps to enable " tproxy "mode in squid ???

with my best regards

---

### Post by SeijiSensei on 2013-02-10
1) Why did you compile your own copy when you could have installed the version in the Ubuntu repositories?

2) When you install from source, most everything ends up in /usr/local.  As I recall squid creates its own /usr/local/squid directory with the server daemon in /usr/local/squid/bin or ../sbin.  

3) The init.d scripts assume that you are using the repository version.  You can browse the script and replace the reference to the daemon with the appropriate entry in /usr/local.

4) If you mean by "tproxy" you want to set up squid to be a "transparent" proxy, the method for doing that varies across squid versions.  Personally I think you should be running squid-3.x rather than any 2.x version.  In 3.x, you append the word "transparent" to the http_port directive in squid.conf.

5)  That's not enough to create a transparent proxy, though.  You need to add an iptables rule to grab outbound HTTP traffic and push it through the cache.  If eth0 points to the Internet side of the proxy, then you would use

```
/sbin/iptables -t nat -A PREROUTING -p tcp -m tcp -o eth0 --dport 80 -j REDIRECT --to-ports 3128
```

if squid is listening on the default port of 3128.  For added security you can add a "-s ip.addr.of.network/mask" to restrict access to the proxy from anything outside your local network.  If your clients are assigned addresses in 192.168.1.0/24 you would enter that for "ip.addr.of.network/mask" above.

Of course, you should already be restricting access to the cache with the "internal_networks" ACL and associated http_access rule.

---

### Post by drvirus on 2013-02-10
> **SeijiSensei said:**
> 1) Why did you compile your own copy when you could have installed the version in the Ubuntu repositories?

2) When you install from source, most everything ends up in /usr/local.  As I recall squid creates its own /usr/local/squid directory with the server daemon in /usr/local/squid/bin or ../sbin.  

3) The init.d scripts assume that you are using the repository version.  You can browse the script and replace the reference to the daemon with the appropriate entry in /usr/local.

4) If you mean by "tproxy" you want to set up squid to be a "transparent" proxy, the method for doing that varies across squid versions.  Personally I think you should be running squid-3.x rather than any 2.x version.  In 3.x, you append the word "transparent" to the http_port directive in squid.conf.

5)  That's not enough to create a transparent proxy, though.  You need to add an iptables rule to grab outbound HTTP traffic and push it through the cache.  If eth0 points to the Internet side of the proxy, then you would use

```
/sbin/iptables -t nat -A PREROUTING -p tcp -m tcp -o eth0 --dport 80 -j REDIRECT --to-ports 3128
```if squid is listening on the default port of 3128.  For added security you can add a "-s ip.addr.of.network/mask" to restrict access to the proxy from anything outside your local network.  If your clients are assigned addresses in 192.168.1.0/24 you would enter that for "ip.addr.of.network/mask" above.

Of course, you should already be restricting access to the cache with the "internal_networks" ACL and associated http_access rule.


hi ,thank you very much for explanation ,
1-
but can you help me how let squid start and stop from /etc/init.d/squid ???

2-
the 2nd issue is ,
i  dont mean with tproxy  as transparent .
but to be accurate , the mode is "transparent tproxy"
i mean that i dont need to make nat as you typed above  , thats why i told you that all my clients go with  thier orifinal ips .

3-
also , squid 2.7 stable can support tproxy mode , i need itsnot only on squid 3 .

with my best regards

---

### Post by drvirus on 2013-02-10
here is a sample  when we use  tproxy mode :

> 
########### Port Config:
http_port 127.0.0.1:62495
http_port x.x.x.242:64395
http_port 64535 transparent tproxy
icp_port 63515


as you see above , i typed word tproxy after the word transparent


with dat can help


with my best regards

---

### Post by drvirus on 2013-02-11
any suggestions ??



regards

---

