---
title: "Installing WINE then wampserver2?"
date: 2008-05-23
forum: General Help
---

### Post by Lamonte on 2008-05-23
Is it possible to install WINEthen install wampserver 2?  I like how wampserver 2 works and if no what other LAMP servers can I use besides XAMPP (Linux version)

---

### Post by dreadlord_chris on 2008-05-23
Installing a WAMP server with Wine on a Linux OS is just silly. You would be better served using the setup already in the repositories.

The following will do this for you (from a terminal):
```
sudo tasksel install lamp-server
```

or you could open Synaptic > Edit > Mark Packages by Task > LAMP Server

You can find more info here:
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

