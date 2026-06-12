---
title: "/etc/hosts blank"
date: 2006-10-07
forum: General Help
---

### Post by syngiun on 2006-10-07
So my question is this,  what are the default contents of /etc/hosts?

While trying to get hibernate working, my system locked. The only option was to power off by holding the pwr button down.  I  also have my root directory on an XFS partition.  I have noticed the contents of any open files get blanked if i have to pwr down after a system lock(likely due to XFS).

Please help me to get Dapper back so I can quit using Windoze to post here.

---

### Post by Fass on 2006-10-07
The default contents of the hosts file:

```
127.0.0.1       localhost
127.0.1.1       [name of your comp]

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by fragos on 2006-10-08
Fass my hosts file got clobered and nothing admin would work.  My friend Google showed that the hostname had to be in the hosts file.  I folllowed directions and put the following in /etc/hosts (my box is Geo)

127.0.0.1       localhost Geo

Are the two lines, below, you recommend equivalent or subtly different from my single one?

127.0.0.1       localhost
127.0.1.1       [name of your comp]

---

