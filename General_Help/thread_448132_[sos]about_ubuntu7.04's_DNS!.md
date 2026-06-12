---
title: "[sos]about ubuntu7.04's DNS!"
date: 2007-05-18
forum: General Help
---

### Post by wanhao1986 on 2007-05-18
i'm new here,and have just installed ubuntu7.04.i'm a red-hat user before,but now i realy don't know how to configure ubuntu's dns.i even don't know where named.conf is,please help me. thanks! and who have unbuntu's configuration documents?   sorry,i think my english is a bit broken:KS,forgive me!

---

### Post by mbradlcu on 2007-05-19
welcome fellow Xredhat user ; )
here's my notes on how to setup a dns server on ubuntu. let me know if you have any questions about it, have fun!
O, and the files you'll want to create/edit can be placed in /var/lib/named/etc/bind/named.conf.local,, it points to my zone files located in a sub-dir called zones

I'm not sure how this one slipped by but here's how I setup bind9 using chroot on appserv1
apt-get install bind9
vi /etc/defaults/bind #change
"-u bind" => "-u bind -t /var/lib/named"
mkdir -p /var/lib/named/etc
mkdir /var/lib/named/dev
mkdir -p /var/lib/named/var/cache/bind
mkdir -p /var/lib/named/var/run/bind/run
mv /etc/bind /var/lib/named/etc
ln -s /var/lib/named/etc/bind /etc/bind
mknod /var/lib/named/dev/null c 1 3
mknod /var/lib/named/dev/random c 1 8
chmod 666 /var/lib/named/dev/null /var/lib/named/dev/random
chown -R bind:bind /var/lib/named/var/*
chown -R bind:bind /var/lib/named/etc/bind
vi /etc/init.d/sysklogd # change
SYSLOGD="-u syslog" => SYSLOGD="-u syslog -a /var/lib/named/dev/log"
/etc/init.d/sysklogd restart
Start up BIND, and check /var/log/syslog for any errors:
/etc/init.d/bind9 start

---

