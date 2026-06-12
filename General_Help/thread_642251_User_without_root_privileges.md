---
title: "User without root privileges"
date: 2007-12-16
forum: General Help
---

### Post by Xi0N on 2007-12-16
Hi all
I have to create a new user in my ubuntu system, but i dont want this user to get root privileges by using commands as sudo or su.
In other words, i dont want him to use his own password to have this kind of privileges.
¿How can i do it?

Thanks

---

### Post by taurus on 2007-12-16
Just don't add his username to groups adm & admin.  Then, he can't use sudo/gksudo.

---

### Post by iris-n on 2007-12-16
This is the standard way users are created, just the first gets root access.
To be certain, in System->Administrarion->Users and Groups, add a new one, and in the User Privileges tab make sure that System Administration is unchecked.

---

### Post by Xi0N on 2007-12-16
Thanks, one more question:

How to make this user unable to "go out" of his /home directory'

Thanks

---

