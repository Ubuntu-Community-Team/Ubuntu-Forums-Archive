---
title: "Change group of user"
date: 2008-06-03
forum: General Help
---

### Post by pospichalales on 2008-06-03
I have linux server with debian. I added new user. Then I added this user to the Samba database. User is at group called Domain Users. How can I change group of user to Domain Administrators?

---

### Post by cmnorton on 2008-06-04
Domain Users is a Windows permissions group. You won't find that in a Linux system.

Your SAMBA users must be mapped to some user on your Linux system, or your SAMBA shares must be accessible to everyone. 

You can create a general-purpose username so all your windows users can log into SAMBA using that name, or actually give each user a Linux username. Then you would map each windows user to the corresponding Linux user.

---

