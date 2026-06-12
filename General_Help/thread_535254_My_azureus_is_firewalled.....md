---
title: "My azureus is firewalled...."
date: 2007-08-26
forum: General Help
---

### Post by elidoperezmd on 2007-08-26
hi all, just installed azureus and says that is firewalled the ##### udp port. how to unfirewalled?

---

### Post by por100pre1 on 2007-08-26
Use Firestarter to open the port.

```
sudo aptitude install firestarter
```

[Here's]("http://www.fs-security.com/docs/interface.php") how to do it.

---

### Post by quux on 2007-08-26
Hi, in case your machine is behind some kind of router try forwarding a UDP port from the external interface of your router to the IP of the internal machine you're running Azureus on in the admin interface of your router. Typically this is part of the router's firewall configuration or called sth. like "port forwarding" or "services".

---

### Post by elidoperezmd on 2007-08-26
hi, thanks for such a quick response.... kind of knew here, i installed the firestarter as you said, but does not show uo in the applications menu, where is it? how it works? how to start it?

---

### Post by southernman on 2007-08-26
The most important question you should respond to is... Does your computer pass through a router on the way to the internet?

---

### Post by elidoperezmd on 2007-08-26
yes it does, i have a speedstream modem and a belkin router
how do i make it work?

and now i just found out that when i open it, all the internet slows down, surfing is almost impossible.... pages will not open
thanks for all the help

---

### Post by southernman on 2007-08-26
> **elidoperezmd said:**
> yes it does, i have a speedstream modem and a belkin router
how do i make it work?

and now i just found out that when i open it, all the internet slows down, surfing is almost impossible.... pages will not open
thanks for all the helpI think you said you got the ports opened in the router and azuerus is no longer firewalled... right?

Apparenly so if your surfing ability went to a crawl. You can't download and upload with the limits set to unlimited or that will happen. On my dsl, I set download to around 50 and upload to around 18. Although the download limit doesn't really affect your surfing ability, if it's to high it will hurt your ratio and may cause you to be blocked by some torrents.

edited/ also if your router supports upnp then disable it. Make sure you also disable it in the azuerus configuration too.

---

### Post by por100pre1 on 2007-08-26
> **elidoperezmd said:**
> hi, thanks for such a quick response.... kind of knew here, i installed the firestarter as you said, but does not show uo in the applications menu, where is it? how it works? how to start it?

**System> Administration> Firestarter**

Sorry for the delay...

---

