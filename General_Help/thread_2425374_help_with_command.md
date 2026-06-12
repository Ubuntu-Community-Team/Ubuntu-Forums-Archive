---
title: "help with command"
date: 2019-08-25
forum: General Help
---

### Post by dondan2 on 2019-08-25
Hi, 


I need help with one question: 

 What complete command allows you to verify that domain users are accessible, that is, that you can log in with them?

Thanks for your help!

---

### Post by cruzer001 on 2019-08-25
Users and groups?

[https://help.ubuntu.com/community/AddUsersHowto#Graphical_Ubuntu](https://help.ubuntu.com/community/AddUsersHowto#Graphical_Ubuntu)

[https://help.ubuntu.com/lts/serverguide/user-management.html#adding-deleting-users](https://help.ubuntu.com/lts/serverguide/user-management.html#adding-deleting-users)

---

### Post by TheFu on 2019-08-25
> **dondan2 said:**
> Hi, 


I need help with one question: 

 What complete command allows you to verify that domain users are accessible, that is, that you can log in with them?

Thanks for your help!

What do you mean by "domain?"  If you mean some sort of LDAP thing, then there isn't any command to verify that someone else knows how to login or not besides actually logging in.

You can get a list of users by using the **getent passwd** command. If the LDAP connection is setup correctly in PAM, it will show all local and LDAP users.  Similarly, **getent group** will work for groups.  NFS is commonly used to provide HOME directory storage to each user via autofs.

In most Linux-centric networks I've seen, they use FreeIPA to manage LDAP user accounts and location of HOME directories. There is a POSIX standard LDAP Schema.

As for DNS domains, that isn't controlled solely by the Linux install.  The routers and public/internal DNS are necessary.  There's also NIS, NIS+, and a few other methods to resolve hosts.  DNS has basically won in the solution space.

Sorry, I can't help with Windows much. We avoid it.

---

