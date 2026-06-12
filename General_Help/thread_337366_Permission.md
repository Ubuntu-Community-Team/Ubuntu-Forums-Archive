---
title: "Permission"
date: 2007-01-12
forum: General Help
---

### Post by deaddylan123 on 2007-01-12
Hey, well im trying to get java installed on firefox, but to get the plugin into the firefox plugin directory, i have to have 'permission'. How do i gain the ability to write to this folder? everything is dimmed such as create new file, etc... Im the only account on this computer.

---

### Post by dcstar on 2007-01-13
> **deaddylan123 said:**
> Hey, well im trying to get java installed on firefox, but to get the plugin into the firefox plugin directory, i have to have 'permission'. How do i gain the ability to write to this folder? everything is dimmed such as create new file, etc... Im the only account on this computer.
Create a new Launcher with the following:
```
gksudo nautilus
```
Then you can use it to copy files with root privileges.

---

