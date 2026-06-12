---
title: "change sudo user's UID"
date: 2008-05-24
forum: General Help
---

### Post by clementvii on 2008-05-24
How can I move the "sudo" user, the user who has the capability to do administrative tasks immediately after a fresh install, to a user with another UID?  It doesn't matter whether the username is transferred to the new user or not.

For example, if the new installation has a sudo user george with a UID of 1000, I'd like to create another user with a UID of 1050, make him the sudo user, and take sudo power away from the user with a UID of 1000.  It doesn't matter whether george has a UID of 1000 or 1050 after the change.

---

### Post by sdennie on 2008-05-24
I believe what you want is:

```

sudo deluser first_user admin
sudo adduser second_user admin

```

You can also do this via the gui though.  System->Administration->Users & Groups.

---

### Post by ibuclaw on 2008-05-24
Personally, I prefer to do it with sed:
```

sudo adduser **newname**
sudo sed -i -e '/:114:/s/**oldname**/**newname**/' /etc/group

```
Creates a new user "newname" and replaces "oldname" with "newname" in the admin group line.
Regards
Iain

---

