---
title: "how to flush DNS cache in 16.04.1"
date: 2016-11-10
forum: General Help
---

### Post by Kris_M on 2016-11-10
how to flush DNS cache in 16.04.1

/etc/hosts is currently
```
127.0.0.1    localhost
127.0.1.1    kris-Z97X-UD3H

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

will this work?
sudo apt-get install nscd
sudo /etc/init.d/nscd restart

EDIT I did the above and /etc/hosts remained the same.  Is that correct?  Thanks!

---

### Post by TheFu on 2016-11-11
/etc/hosts isn't DNS. It is a static file unless you manually change it.

The /etc/nsswitch.conf file controls the order of name resolution. Usually the hosts file is checked BEFORE DNS or other methods.

Changes to DNS are usually picked up quickly enough that I've never needed to flush any cache. The nscd manpage says any changes to the hosts file will be picked up after a short delay. Non-standard server resolution methods might need a **nscd -i ** to flush the cache and reload.  I've never needed this.

I'm curious. What did you expect to happen?

---

### Post by Kris_M on 2016-11-11
the idea is that the DNS cache might be full of junk and causing extra accesses on the way to resolving a single name for an internet access.

the /etc/nsswitch.conf is not what I'm looking for
```
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat
gshadow:        files

hosts:          files dns
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
```


EDIT  
/etc/NetworkManager/dnsmasq.d  is empty.

---

### Post by TheFu on 2016-11-11
And **nscd -i** (as mentioned above) doesn't do what you want?  According to the manpage, it should. May need to provide some other options. I dunno.

Could there be 2 dns caching services running?  nscd is one. Dnsmasq could be another, if configured that way. I'd check the log files and lsof to see which actually got the DNS port.

---

### Post by Kris_M on 2016-11-11
actually, neither are running - dnsmasq is apparently off by default and I restored to before I installed nscd.

---

### Post by SeijiSensei on 2016-11-11
We had this discussion a few weeks' back: [https://ubuntuforums.org/showthread.php?t=2338500](https://ubuntuforums.org/showthread.php?t=2338500)

My opinion remains the same, that flushing the DNS cache in Linux is unnecessary.  The only time I've ever had an issue with DNS resolution is when I change an A record on my DNS server.  Linux doesn't have any of the DNS-caching problems that Windows is prone to.

---

### Post by Kris_M on 2016-11-11
okay, I'll mark this solved and forget it.

---

### Post by eythian on 2017-01-13
> **SeijiSensei said:**
> My opinion remains the same, that flushing the DNS cache in Linux is unnecessary.  The only time I've ever had an issue with DNS resolution is when I change an A record on my DNS server.  Linux doesn't have any of the DNS-caching problems that Windows is prone to.

It'd be good to have some solution. For example, you create a CNAME and try to load it in your browser too quickly, before the DNS server has picked it up. Now you have have a negatively cached record until the TTL expires. Flushing the DNS cache would save this. Obviously the reverse happens too, where you change the IP something points to and want to check the change immediately.

DNS caching isn't a broken windows thing, it's a perfectly normal way of DNS working. Sometimes you have reasons to bypass it. "You don't need to do it" is not right, and not a solution.

---

### Post by tcorneli on 2017-02-24
> **eythian said:**
> It'd be good to have some solution. For example, you create a CNAME and try to load it in your browser too quickly, before the DNS server has picked it up. Now you have have a negatively cached record until the TTL expires. Flushing the DNS cache would save this. Obviously the reverse happens too, where you change the IP something points to and want to check the change immediately.

DNS caching isn't a broken windows thing, it's a perfectly normal way of DNS working. Sometimes you have reasons to bypass it. "You don't need to do it" is not right, and not a solution.

Agreed. It takes way too much time to wait for the TTL to pass.

---

### Post by SeijiSensei on 2017-02-24
On my pretty vanilla 14.04 and 16.04 machines, dnsmasq is running with --cache-size=0 which disables caching entirely.  

According to [http://stackoverflow.com/questions/11020027/dns-caching-in-linux](http://stackoverflow.com/questions/11020027/dns-caching-in-linux), there is no OS-level DNS caching in Linux either, unless nscd is running which is not the case on any of my machines.

---

