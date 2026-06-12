---
title: "Apache2 PHP4 and mysql"
date: 2005-10-17
forum: General Help
---

### Post by crow on 2005-10-17
I folowed this howto in Wiki for installing LAMP : [https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29]("https://wiki.ubuntu.com/ApacheMySQLPHP?highlight=%28apache%29")

Apache2 install fine but then come to php4 i get this:
```

sudo apt-get install php4
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package php4

```
Is there any NEW Howto install LAMP on Breeyz Badger 5.10.

Thnx

---

### Post by indispus on 2005-10-17
Check your repositories!

---

### Post by seldenthuis on 2005-10-17
php4 is in 'universe', so you'll have to enable that in /etc/apt/sources.list.

---

