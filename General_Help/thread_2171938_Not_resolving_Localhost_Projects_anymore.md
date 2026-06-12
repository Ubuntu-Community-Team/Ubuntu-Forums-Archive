---
title: "Not resolving Localhost Projects anymore"
date: 2013-09-02
forum: General Help
---

### Post by mario12 on 2013-09-02
Hello, 

I am having a problem I can't resolve my localhost projects anymore. (a reboot might deleted some configuration)

My server is NS too for the local network. All of the outbound requests are Resolved successfully.

I don't know where to start but here is a view from some of my files :

**Hosts:**

```

127.0.0.1       localhost
127.0.0.1       mydomain.mydomain.local       mydomain



# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

/etc/resolvconf/resolv.conf/base

```

domain mydomain.local
search mydomain.local
# nameserver 192.168.0.253
nameserver 127.0.0.1

```

Any guide and help would be appreciated.

---

