---
title: "FireHOL not starting..."
date: 2006-11-02
forum: General Help
---

### Post by Spudgun on 2006-11-02
When I try to run FireHOL by issuing the command...
```
sudo /etc/init.d/firehol start
```

... I get the following error:
```
Starting iptables firewall: FireHOL ...Stopping: /etc/default/firehol forbids it.
done.
```

Anyone got any ideas how to fix this?

---

### Post by Spudgun on 2006-11-05
Anyone?

---

### Post by Spudgun on 2006-11-06
Bump...

---

### Post by Spudgun on 2006-11-07
Ah well, never mind.

---

### Post by Morphius on 2007-01-18
Please take a look at /etc/default/firehol using vim. This is what is preventing firehol from starting. Line one to be precise.

---

