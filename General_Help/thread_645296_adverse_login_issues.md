---
title: "adverse login issues"
date: 2007-12-19
forum: General Help
---

### Post by sdb2028 on 2007-12-19
I have poked where I should not have. Now I cannot login, Can't even get to the login screen. Boots fine, then displays a box stating "No serving hosts were found" with an "Add host" input box. Apparently I turned on "XDMCP". How might I fix this issue. Can I unpoke where I shouldn't have?

---

### Post by sdb2028 on 2007-12-19
Fixed it!! deleted /etc/gdm/gdm.conf-custom, restarted gdm

---

