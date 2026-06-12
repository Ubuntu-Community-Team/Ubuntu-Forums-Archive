---
title: "Postfix Error"
date: 2008-05-26
forum: General Help
---

### Post by Black Mage on 2008-05-26
I am getting this error in postfix and I was wondering if anyone could help or know what the problem is?

The Error:
May 26 13:45:51 mainserver postfix/smtpd[6349]: fatal: bad net/mask pattern: "192.168.1.0/202"

And I have two servers on my network. The mainserver ip being 192.168.1.201 and the web server ip of 192.168.1.202

---

### Post by Gunman1982 on 2008-05-26
192.168.1.0/202 <- The 202 is wrong, you can change it to 24, that should do the trick.

---

