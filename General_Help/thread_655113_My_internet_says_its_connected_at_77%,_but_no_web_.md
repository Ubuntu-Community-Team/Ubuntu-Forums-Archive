---
title: "My internet says its connected at 77%, but no web pages load  anything."
date: 2007-12-31
forum: General Help
---

### Post by Backthen on 2007-12-31
WHats the deal guys?

---

### Post by foolsh on 2008-01-01
Some more information please
what is your setup?
what kind or internet connection? dail-up? broadband?
is there a router between your computer and the internet?

---

### Post by Ozeuss on 2008-01-01
also,
is synaptic working properly, or any other app that uses the network? that way your problem is limited to a browser problem.

---

### Post by ronmarley1 on 2008-01-01
This happens to me every once in a while.  Since you indicate that the connection is 77%, I'm assuming it's wireless.  To solve the issue for myself, my first choice is to disconnect and then reconnect to my router (even though nm-applet indicates a connection).  If this does not fix the problem, I cycle my wireless router (LinkSys) and then I'm good to go.
Sorry for the non-solution, but it happens so rarely for me, I've never really dug into the cause.

---

### Post by lswest on 2008-01-01
um, try getting an ip with ```
sudo dhclient [name of device] 
``` happens to me sometimes when i connect to the lan, and only get lan functionality (e.g. no internet).  basically it just requests a new IP from the dhcp server of your router.

---

### Post by wag_ on 2008-01-01
Try disabling IPv6:

```
 
sudo -s 
echo "" >> /etc/modprobe.d/blacklist
echo "blacklist ipv6" >> /etc/modprobe.d/blacklist
exit

```

---

