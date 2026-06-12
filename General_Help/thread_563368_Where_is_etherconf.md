---
title: "Where is etherconf"
date: 2007-09-29
forum: General Help
---

### Post by satimis on 2007-09-29
Hi folks,


Ubuntu 7.04 server amd64

Where is etherconf?

$ apt-cache policy etherconf
$ apt-cache search etherconf
without printout

Thanks


satimis

---

### Post by g2g591 on 2007-09-30
first of all, what type of thing is etherconf, a package , or configuration file?

---

### Post by satimis on 2007-09-30
> **g2g591 said:**
> first of all, what type of thing is etherconf, a package , or configuration file?
A package.  Please refer to 

a) Install etherconf:
# apt-get install etherconf

of;

[http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html](http://www.cyberciti.biz/tips/how-do-i-run-firewall-script-as-soon-as-eth0-interface-brings-up.html)


B.R.
satimis

---

### Post by Soarer on 2007-09-30
It is on Debian, but not in the Ubuntu repos, as far as I can see.

Does ethtool do the same thing?

---

### Post by satimis on 2007-09-30
> **Soarer said:**
> It is on Debian, but not in the Ubuntu repos, as far as I can see.

Does ethtool do the same thing?
Tks for your advice.

$ apt-cache policy ethtool```

ethtool:
  Installed: 5-1build1
  Candidate: 5-1build1
  Version table:
 *** 5-1build1 0
        500 http://us.archive.ubuntu.com feisty/main Packages
        100 /var/lib/dpkg/status

```
Already installed.

$ which ethtool
/usr/sbin/ethtool

$ sudo dpkg-reconfigure ethtool
Password:
No printout

$ which dpkg-reconfigure
/usr/sbin/dpkg-reconfigure


Is the command line NOT correct?  TIA


satimis

---

### Post by Soarer on 2007-09-30
try:

```
ethtool -h
```

or

```
man ethtool
```


I expect it will have to be run with 'sudo' to actually change settings.

---

