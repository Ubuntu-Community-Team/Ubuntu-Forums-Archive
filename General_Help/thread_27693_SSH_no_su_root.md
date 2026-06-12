---
title: "SSH no su root"
date: 2005-04-17
forum: General Help
---

### Post by geekgod on 2005-04-17
i installed open SSH package and am connecting to it with putty.. i can connect to it with my user account but when i try to logon as root or su to root it asks for a password... then says authentication denied.  I added root to rhe SSH group then rebooted no luck still same and both pc's are on lan with same subnet.

---

### Post by speedman on 2005-04-17
ssh in as your regular user (who has admin group status) and use:

sudo -s

... to get a root shell.


Regards,

SM

---

### Post by geekgod on 2005-04-18
[QUOTE=speedman]
sudo -s
... to get a root shell.

[/QUOTE]


awsome thanks

---

