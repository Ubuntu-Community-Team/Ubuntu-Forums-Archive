---
title: "adsl"
date: 2005-10-14
forum: General Help
---

### Post by vsevolod_xxx on 2005-10-14
Hello sorry my english is very very bad....]
 I have adsl modem, and i can't setup internet conection..
Could anybody help me to config it? Modem use protokol PPPoE, and connect with computer on ethernet...

---

### Post by adwait on 2005-10-14
If it is just a modem(ie: it doesn't automatically connect to your ISP, or perform as a DNS server etc), then you can use pppoeconf:
```
sudo pppoeconf 
```

If it automatically connects to your ISP (since you have mentioned that the MODEM uses pppoe, then just add the IP address of the modem to your /etc/resolv.conf file.
```
sudo gedit /etc/resolv.conf
```
Add it as:
> nameserver <ip address>

---

### Post by vsevolod_xxx on 2005-10-15
Thank you, now its working. And i Have another problem: some pages is not opening by browser, but at the same time this pages is opening by ms-windows InternetExplorer.  How i can fix this problem?

---

### Post by flygirlnz on 2005-10-15
I have a DSL-200 revision B modem and I did try the suggested sudo pppoeconf, but it did not work for me.

Any more suggestions?

---

### Post by vsevolod_xxx on 2005-10-15
Try make ping to your server, maybe it help you...:
ping <ip your server>

---

