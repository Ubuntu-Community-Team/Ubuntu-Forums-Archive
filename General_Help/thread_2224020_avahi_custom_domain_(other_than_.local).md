---
title: "avahi custom domain (other than .local)"
date: 2014-05-14
forum: General Help
---

### Post by frankie3 on 2014-05-14
Hi, 

Recently I've started with avahi and have to say I'm pretty impressed. But, it works only for domain ".local". 

The man page for avahi ([http://manpages.ubuntu.com/manpages/hardy/man5/avahi-daemon.conf.5.html](http://manpages.ubuntu.com/manpages/hardy/man5/avahi-daemon.conf.5.html)) claims that there something like **domain-name= **which kind of suggests that I can change this to something else than ".local"

Having config like this 
```

[server]
#host-name=foo                                                                                                                                                                                                       
#domain-name=local                                                                                                                                                                                                                                                                                                                                                                           
use-ipv4=yes
use-ipv6=yes
```

Things works as expected

```

myhost@user:~$ ping myhost.local
PING myhost.local (192.168.0.105) 56(84) bytes of data.
64 bytes from myhost.local (192.168.0.105): icmp_seq=1 ttl=64 time=0.044 ms
64 bytes from myhost.local (192.168.0.105): icmp_seq=2 ttl=64 time=0.038 ms
```

But when I change my domain to something else let say **domain-name=**mydomain

```

[server]
#host-name=foo                                                                                                                                                                                                       
domain-name=mydomain                                                                                                                                                                                                                                                                                                                                                                           
use-ipv4=yes
use-ipv6=yes
```

restart 

```

:$ sudo service avahi-daemon restart
avahi-daemon stop/waiting
avahi-daemon start/running, process 4065
```

The host is no longer there

```

myhost@user:~$ ping myhost.mydomain
ping: unknown host myhost.mydomain
```

Since local is working fine, why I need this? So some ISP figured that is good idea, to manage .local on their side, I know that common advice is to contact them and say that is wrong. It won't work here. 

Question is: is there a way to handle something else than ".local" as domain by avahi.

---

