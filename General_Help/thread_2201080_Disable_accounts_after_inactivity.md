---
title: "Disable accounts after inactivity"
date: 2014-01-22
forum: General Help
---

### Post by vendethiel on 2014-01-22
Is there anyway to automatically disable accounts after 30 days of inactivity in Ubuntu 12.04?

---

### Post by deadflowr on 2014-01-22
set a passwd with the inactive option
```
man passwd
```

Added example
```
sudo passwd -i 30 username
```
That should set the password to expire after 30 days.

---

