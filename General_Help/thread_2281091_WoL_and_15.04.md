---
title: "WoL and 15.04"
date: 2015-06-04
forum: General Help
---

### Post by pingaan on 2015-06-04
Hi,

Running "sudo ethtool -s  wol g" works ike a charm if I do it manually after boot up but if I enter it in crontab, like I did before upgrading Ubuntu it doesn't. 
Is there something new concerning crontab that I should know about?

Cheers.

---

### Post by Bucky Ball on 2015-06-04
*Thread moved to **General Help**.*

---

### Post by tgalati4 on 2015-06-05
Don't know about *crontab* changes in 15.04, but you could try putting it in /etc/rc.local (without the sudo).  That has worked for me on Dell PowerEdge servers.

---

### Post by pingaan on 2015-06-06
Worked like a charm.
Cheers!

---

