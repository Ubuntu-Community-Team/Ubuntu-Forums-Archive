---
title: "[SOLVED] sudo &amp;quot;&amp;quot;&amp;quot;&amp;quot;: unable to resolv host name mattia-desktop"
date: 2008-03-03
forum: General Help
---

### Post by mkgkg on 2008-03-03
when i write sudo and something else into shell, the answer was : sudo: unable to resolve host mattia-desktop

---

### Post by Arthur Archnix on 2008-03-03
what's the output of:
```
cat /etc/hosts
```

---

### Post by mkgkg on 2008-03-03
127.0.0.1 localhost
127.0.1.1 mattia-desktop.local

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Arthur Archnix on 2008-03-03
```
sudo cp /etc/hosts /etc/hosts.bak
gksudo gedit /etc/hosts
```
and delete the .local so that it looks like this:
> 127.0.0.1 localhost
127.0.1.1 mattia-desktop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

Oops... hehe.. you can't use sudo. Ok, boot into the recovery console and type this:
```
cp /etc/hosts /etc/hosts.bak
nano /etc/hosts
```

---

### Post by mkgkg on 2008-03-03
okkkkkkkkkkk...thank you...now everything it's ok.

---

### Post by agent8131 on 2008-04-24
See **[Ubuntu Bug #32906]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/32906")**

---

