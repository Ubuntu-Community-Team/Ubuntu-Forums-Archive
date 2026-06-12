---
title: "User not created after dist install from remastersys"
date: 2008-05-21
forum: General Help
---

### Post by danstah on 2008-05-21
I created a dist disc from remastersys but it does not seem to create the user i entered when doing the install..  So when i go to login it acts as if that user does not exist. Is there a fix for this?

---

### Post by sdennie on 2008-05-21
I don't know if there is a fix for the installation but, if the system is booting, you could start it in recovery mode (should be an option from the grub menu) and then do:

```

adduser some_user_name
addgroup some_user_name admin

```

That should create you a user with sudo privledges.

---

