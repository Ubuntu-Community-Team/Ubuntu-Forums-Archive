---
title: "Gimp?"
date: 2016-12-09
forum: General Help
---

### Post by JerseyDevil82 on 2016-12-09
Is Gimp no longer available in the software centre?

---

### Post by howefield on 2016-12-09
Thread moved to the "*General Help*" forum.

Which version of Ubuntu are you using ?

Gimp should be available to install via the Software Centre and also from terminal if you don't mind using the command line.

```
apt-cache show gimp
```

will give you the version and package details and..

```
sudo apt-get install gimp
```

---

### Post by JerseyDevil82 on 2016-12-09
> **howefield said:**
> Thread moved to the "*General Help*" forum.

Which version of Ubuntu are you using ?

Gimp should be available to install via the Software Centre and also from terminal if you don't mind using the command line.

```
apt-cache show gimp
```

will give you the version and package details and..

```
sudo apt-get install gimp
```

16.10

---

### Post by oldos2er on 2016-12-09
Gimp is in the universe repository, so be sure you have that enabled.

---

### Post by cariboo on 2016-12-09
If you want to check if a package is available in the repositories, have a look at [packages.ubuntu.com]("http://packages.ubuntu.com/")

---

