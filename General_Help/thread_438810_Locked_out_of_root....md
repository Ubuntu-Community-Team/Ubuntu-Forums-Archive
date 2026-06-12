---
title: "Locked out of root..."
date: 2007-05-10
forum: General Help
---

### Post by Valeranth on 2007-05-10
I really dont know what happened, but after this morning I can no longer become a super user. I have never changed the root password, so I would simply require my password to become a superuser, however now when I input this I gives me a error. Anything I can do?

---

### Post by ewankho on 2007-05-10
I think if you boot in recovery mode from grub you get access to root, if you have the default setup.

---

### Post by bapoumba on 2007-05-10
Boot in recovery mode. You'll be root with a # prompt. Run:
```
# adduser <your_login_here> admin
# reboot
```

More infos: [http://www.psychocats.net/ubuntu/sudo]("http://www.psychocats.net/ubuntu/sudo")

---

