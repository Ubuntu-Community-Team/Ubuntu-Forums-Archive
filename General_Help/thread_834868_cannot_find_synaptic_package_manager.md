---
title: "cannot find synaptic package manager"
date: 2008-06-19
forum: General Help
---

### Post by dbauer88 on 2008-06-19
Quite simply, I cannot find synaptic package manager under 'system' > 'administration' where it normally is. Additionally, under 'applications' the 'install or remove applications' option is missing. I was thinking it was a user privilege issue, but whenever I try to authenticate or unlock the 'users and groups' I receive an error message: "could not authenticate--an unexpected error has occurred". :confused: So, any help in this matter would be greatly appreciated.

Currently using Ubuntu 8.04 LTS on a Toshiba Satellite A105-S4324.

---

### Post by iaculallad on 2008-06-19
Try installing the policykit:

```
sudo apt-get install policykit policykit-gnome
```

---

### Post by Happy_Man on 2008-06-19
Right-click your menu, click 'edit menus' and then go to System --> Administration and make sure the Synaptic option is checked.

---

