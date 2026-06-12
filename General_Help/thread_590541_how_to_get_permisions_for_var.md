---
title: "how to get permisions for /var"
date: 2007-10-24
forum: General Help
---

### Post by tynen on 2007-10-24
This is kind of a nooby questions, but how would I paste files into /var/www/apache2-default? i don't have permissions for it, but my user account is root.

---

### Post by taurus on 2007-10-24
Applications -> Accessories -> Terminal
```
sudo cp **filename** /var/www/apache2-default
```

Or

<Alt>F2 and type

```
gksudo nautilus
```
and just drag the file to /var/www/apache2-default directory.

---

### Post by tynen on 2007-10-24
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo cp **filename** /var/www/apache2-default
```

Or

<Alt>F2 and type

```
gksudo nautilus
```
and just drag the file to /var/www/apache2-default directory.

Thank you very much!! =] I need to have a website up by tomorrow for school. =D I just recently got involved with ubuntu 7.10 I've got apache installed. Hopefully I can get this all to work right =P

---

