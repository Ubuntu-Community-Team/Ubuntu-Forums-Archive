---
title: "I don't understand the 'hostname' problem - help please?"
date: 2007-10-16
forum: General Help
---

### Post by dryder on 2007-10-16
Hi,

I have read where people have tried to change their hostname or resolve the 'Can't get fully qualified hostname' problem only to end up in trouble.

I am now getting the same message but not after I have changed any names or config files.

These are my /etc/hosts and etc/hostname files:

/etc/hosts:
> 127.0.0.1 localhost
127.0.1.1 ubuntu-server.CEDARS

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.2 *name1*
192.168.0.3 *name2*
192.165.0.4 *name3*
192.168.0.5 *name4*
(italics substituted for computer names)
/etc/hostname:
> ubuntu-server

Could some kind person please help by telling me (explaining? :-) ) what I need to change to have a proper 'hostname'?

I know there are numerous posts on this but there are numerous posts of people being unable to properly use their systems because the configuration is wrong.

Many thanks,

David

---

### Post by yabbadabbadont on 2007-10-16
Try changing ```
127.0.1.1 ubuntu-server.CEDARS
``` to ```
127.0.1.1 ubuntu-server.CEDARS  ubuntu-server
```
As an example, here is my config:
```
/home/daffy $ head /etc/hosts
127.0.0.1       localhost
127.0.1.1       yoiks.and.away  yoiks

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
/home/daffy $ cat /etc/hostname 
yoiks
/home/daffy $ dnsdomainname 
and.away
/home/daffy $ hostname 
yoiks
/home/daffy $ hostname -f
yoiks.and.away

```

---

### Post by dryder on 2007-10-16
Hi yabbadabbadont - thanks for replying.

> Try changing
Code:

127.0.1.1 ubuntu-server.CEDARS

to
Code:

127.0.1.1 ubuntu-server.CEDARS  ubuntu-server



I'll try - and hopefully reboot .. :-)

David

---

### Post by dryder on 2007-10-16
I rebooted OK but now OpenOffice tells me user 'david' (that's me) must stop using OpenOffice "before continuing" or my settings may be lost..

Any thoughts?

David

---

### Post by yabbadabbadont on 2007-10-16
> **dryder said:**
> Any thoughts?

Lots and lots, but none that are relevant to your new issue.  :D

You should probably start a new thread about this new issue.  Especially if your hostname problem has been resolved.

---

### Post by dryder on 2007-10-17
> Lots and lots, but none that are relevant to your new issue. 

ROTFL! 

Will post a new thread as you suggest.

---

