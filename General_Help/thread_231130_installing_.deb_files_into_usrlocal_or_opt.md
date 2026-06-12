---
title: "installing .deb files into /usr/local or /opt"
date: 2006-08-07
forum: General Help
---

### Post by henriqueqc on 2006-08-07
Hello!
I'am trying to install some packages that are not part of the default set of Ubuntu repositories. And as beeing so I think they deserve to be separeted from the "distribution" packages in a directory like /usr/local or /opt. I've been reading that this separation is a common practice (correct me if I'am wrong).
I think maybe this can be done with "dpkg" but I don't know how.
Does someone got a hint?
Thanks!

---

### Post by aysiu on 2006-08-07
It's not a common practice for .deb files--mainly for .tar.gz files.

If you do ```
sudo dpkg -i *packagename*.deb
``` or double-click the .deb and install it with GDebi, it will show up in your list of installed packages, and you can remove it with Synaptic, Adept, *aptitude*, or *apt-get*: ```
sudo aptitude remove *packagename*
```

---

### Post by temcat on 2006-08-07
Unfortunately, most apps have paths hardcoded in them, so they won't work even if you manage to install them in another place. You can, however, compile the app from source and specify the path on configure stage:

```
./configure --prefix=/usr/local
```

Using checkinstall, you can even make a .deb which will install in the right place (though it will not be a full-featured one, that is, it will not have any dependencies).

However, even with source install you're not guaranteed from integration problems between your app and the distro. These are outlined here:

[http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support]("http://plan99.net/autopackage/What_can_distributions_do_to_fix_broken/usr/local_support")

---

