---
title: "How do I unlock two &quot;Access Denied&quot; Files."
date: 2007-11-13
forum: General Help
---

### Post by El Muelio on 2007-11-13
I need to edit these to install my BB modem:

 /etc/ppp/chap-secrets
 /etc/ppp/pap-secrets

It says Access Denied when I type that into the Terminal, any ideas how I can unlock them?

---

### Post by taurus on 2007-11-13
Applications -> Accessories -> Terminal
```
gksudo gedit /etc/ppp/chap-secrets
```

---

### Post by Joeb454 on 2007-11-13
try typing```
sudo gedit /etc/your/filelocation
```

---

### Post by El Muelio on 2007-11-13
Thanks very much guys, hopefully the next time I post here will be from within the relms of my 40gb Ubuntu HD.

---

