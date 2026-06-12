---
title: "Root User"
date: 2008-02-18
forum: General Help
---

### Post by anksi4u on 2008-02-18
How do we login as root user without the terminal...

---

### Post by SunnyRabbiera on 2008-02-18
By default the root user is disabled, its possible to get root running but at your own risk.
Sorry there is not a easier way to enter superusuer mode... yet.

---

### Post by SpaceTeddy on 2008-02-18
yes there is... but i have t agree that it is not for the light hearted or the quick hand with commands...

having that said, one more needs to be said.
**DO NOT USE ROOT UNLESS YOU NO OTHER CHOICE !!!**


to attain a root shell, use one of the following commands
> sudo su
sudo bash

enter your password when ask for a password - you should be root now !

---

### Post by pointone on 2008-02-18
```
sudo passwd root
```

This will allow you to set a password for the root account; effectively enabling it. You can then login as root in your desktop environment of choice.

It's not recommended, though; big security risk and whatnot.

---

