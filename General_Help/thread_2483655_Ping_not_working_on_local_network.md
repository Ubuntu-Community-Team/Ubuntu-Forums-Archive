---
title: "Ping not working on local network"
date: 2023-02-05
forum: General Help
---

### Post by glb1945 on 2023-02-05
I just installed a new version of Ubuntu 22.04. Ping works on 8.8.8.8 and google.com, but not for my router or printer.
Any help would be appreciated.

---

### Post by MAFoElffen on 2023-02-06
Are we talking a wired or wifi connection?

first, if wired, check to see if you have a green light beside where the wire plugs in... Then
```

/sbin/ip addr |  grep -e '^[[:space:][1-9]:.*UP,LOWER_UP' | sed 's/.*virb.*:.*\|.*lo:.*LOOPBACK.*//g' |         sed -e /^$/d

```
That will show with network devices are up.

Next do
```

ip a
traceroute www.google.com
awk '{print $0}' /proc/net/dev 
awk '{print $0}' /proc/net/route 

```

---

### Post by glb1945 on 2023-02-06
Wireless connection. Note my new post in Networking. This appears to be a bug in 22.04. After a vanilla install ping works for external sites but not for lan. Using the work around indicated by a different user (see post) ping also worked for lan.

---

