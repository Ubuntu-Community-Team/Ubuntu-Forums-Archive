---
title: "I Don't Want Any Firewall"
date: 2007-03-08
forum: General Help
---

### Post by dgore on 2007-03-08
Just installed Ubunta 6.10.  From reading other posts I see that default is all ports are closed.  How do I open all ports and leave them open.

I have a hardware firewall so I don't need any firewall on the operating system.

Thanks

---

### Post by taurus on 2007-03-08
Install firestarter and use it to reconfigure iptables then.

```
sudo aptitude update
sudo aptitude install firestarter
```

---

### Post by melancholeric on 2007-03-08
Actually, I believe iptables is by default configured to leave all ports open, but since there are no services listening to any ports it amounts to having all ports closed.

---

