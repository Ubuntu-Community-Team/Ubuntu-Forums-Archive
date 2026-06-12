---
title: "Set password minimum length"
date: 2008-05-11
forum: General Help
---

### Post by lordjoe_com on 2008-05-11
I am setting up an account for a friend who is used to a 5 letter password. 
I am ok with a los security password but the system will not allow a password that short (except for the user on install) How to a reset the minimum length of an allowed password and lower other security criteria for passwords

---

### Post by Monicker on 2008-05-11
Take a look at /etc/pam.d/common-password.  It has options for controlling password criteria.

Note:  I just tested this, and was able to lower the minimum length required by adding min=3 to the line regarding pam_unix.so. Depending on how much you lower it, you may also have to remove the "obscure" option, or it will complain about the password being too simple.

---

