---
title: "DNS Server Settings"
date: 2008-02-14
forum: General Help
---

### Post by Colin Erith on 2008-02-14
Greetings All
I have just installed Ubuntu 7.10 and am having problems with the internet connection as my provider Vodafone UK Ltd does not support Linux and refuses to provide IP&DNS Server settings. Does anyone have a set of settings that will get me on line, as I seem to have fallen at the first hurdle.

Colin Erith

---

### Post by tcpip4lyfe on 2008-02-14
Are you directly connecting your ubuntu box though a modem or are you going though a router?  Those setting should be provided automatically VIA dhcp.  If you are connecting the modem to the ubuntu box type:

```
sudo /etc/init.d/networking restart
```


and paste the output.

---

### Post by mike555 on 2008-02-14
For dns numbers you can use these ;

      208.67.222.222         ,             208.67.220.220

---

