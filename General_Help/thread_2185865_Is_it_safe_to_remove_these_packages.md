---
title: "Is it safe to remove these packages?"
date: 2013-11-04
forum: General Help
---

### Post by hotwheels14901 on 2013-11-04
Whenever I use apt to install something it gives me the autoremove message:

```
The following packages were automatically installed and are no longer required: 
  libssl-dev libssl-doc linux-headers-3.8.0-29 linux-headers-3.8.0-29-generic 
  linux-headers-3.8.0-30 linux-headers-3.8.0-30-generic 
  linux-image-3.8.0-29-generic linux-image-3.8.0-30-generic 
  linux-image-extra-3.8.0-29-generic linux-image-extra-3.8.0-30-generic 
Use 'apt-get autoremove' to remove them.
```

Are these packages safe to remove or should I not remove them?

---

### Post by oldos2er on 2013-11-04
Yes, it's safe. From ```
man apt-get
``` **autoremove**: autoremove is used to remove packages that were automatically installed to satisfy dependencies for other packages and are now no longer needed.

---

### Post by Bashing-om on 2013-11-04
hotwheels14901; Hi ! Welcome to the forum.

The package manager does not lie. Not only is it safe to remove them, the package manager encourages you to do so ..at the administrators (yours) discretion. That conserves disk space and system resources.
```

sudo apt-get autoremove

```
 For clarification see:
```

man apt-get

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2013-11-04
apt does a pretty good job.  I've never had an issue with autoremove in several years of using it.

---

