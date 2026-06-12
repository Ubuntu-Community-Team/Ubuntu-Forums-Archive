---
title: "How to revert back to Gnome"
date: 2006-11-23
forum: General Help
---

### Post by deekay on 2006-11-23
i installed ubuntu edgy and then updated via synaptic to install kde desktop.
now its logging in KDE by default. i want default login GNOME. how can i revert back to GNOME as my default login ?

---

### Post by Joe_CoT on 2006-11-23
You should just be able select gnome from the login menu (the "sessions" dropdown), and then set that as your default login.

If you're currently using kdm for login, and want to use gdm, do:

```
sudo dpkg-reconfigure gdm
```

Which should set gdm as the default. Either should let you log in to either desktop

---

