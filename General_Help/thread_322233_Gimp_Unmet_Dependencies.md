---
title: "Gimp Unmet Dependencies"
date: 2006-12-20
forum: General Help
---

### Post by OffHand on 2006-12-20
Hi 
I'm trying to install the gimp-svg plugin but it refuses to install because of an unmet dependency. Could anyone help me with this one?

The following packages have unmet dependencies:
  gimp-svg: Depends: gimp (= 2.2.13-1ubuntu1) but 2.2.13-1ubuntu3 is to be installed
E: Broken packages

---

### Post by raul_ on 2006-12-20
Try 
```

apt-get -f install

```

---

### Post by OffHand on 2006-12-20
> **raul_ said:**
> Try 
```

apt-get -f install

```

sudo apt-get -f install gimp-svg does not work.

---

### Post by raul_ on 2006-12-20
without any arguments

---

### Post by OffHand on 2006-12-20
> **raul_ said:**
> without any arguments

That did not help either.

---

### Post by raul_ on 2006-12-20
Strange :-k that should take care of your broken packages..didn't install anything at all? Did you try installing gimp 2.2.13-1ubuntu3 manually?

---

### Post by OffHand on 2006-12-20
> **raul_ said:**
> Strange :-k that should take care of your broken packages..didn't install anything at all? Did you try installing gimp 2.2.13-1ubuntu3 manually?

Nope, just offered to remove some packages. Removing those didn't help. I havn't tried installing it manually but I cannot find the package either.

---

### Post by raul_ on 2006-12-20
It seems that gimp-svg depends of an older version of gimp, and it isn't compatible with the new one (hence the = and not <=) I guess the only solution is either searching for a more recent version of the plugin or uninstalling gimp from the repos, and reinstalling the old version manually.

---

### Post by raul_ on 2006-12-20
[http://linuxappfinder.com/package/gimp-svg]("http://linuxappfinder.com/package/gimp-svg")

---

### Post by OffHand on 2006-12-20
I found the solution to my problem here: [https://launchpad.net/distros/ubuntu/+source/gimp/+bug/56393](https://launchpad.net/distros/ubuntu/+source/gimp/+bug/56393)

---

### Post by sumitkar on 2006-12-20
Yes that's it

---

### Post by cully on 2007-01-16
I had the same problem.  I just added 'universe' to my edgy-updates line and was able to install gimp-svg:

```
deb http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe
```

---

