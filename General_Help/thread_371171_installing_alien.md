---
title: "installing alien"
date: 2007-02-26
forum: General Help
---

### Post by tocilog on 2007-02-26
so i tried installing alien using sudo apt-get install alien but this came up:

```
sudo apt-get install alien
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  alien: Depends: debhelper (>= 3) but it is not going to be installed
         Depends: dpkg-dev but it is not going to be installed
E: Broken packages

```

so what do i do from here?

---

### Post by taurus on 2007-02-26
Try

```
**sudo aptitude update**
sudo aptitude install alien
```

---

### Post by tocilog on 2007-02-26
thanks it worked!

---

