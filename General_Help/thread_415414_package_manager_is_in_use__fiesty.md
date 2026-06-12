---
title: "package manager is in use ? fiesty"
date: 2007-04-20
forum: General Help
---

### Post by guest5 on 2007-04-20
I got an error installing..  I selected both firefox and samba. something about not being able to install due to breaking something, while firefox is listed in kmenu, neither are  installed in adept, of course it is unusable. 

I thought I would reinstall it, but get an error saying I will not be able to change my system settings in any way because another process is using the packaging system database.

I  am wondering if this is a common issue, and what I might do to correct it?

Thanks in advance.

---

### Post by guest5 on 2007-04-20
Solution was ~

"you must manually run 'dpkg --configure -a' to correct the problem."

---

