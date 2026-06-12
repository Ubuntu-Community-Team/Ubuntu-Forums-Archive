---
title: "qtcreater does not display any examples"
date: 2013-07-03
forum: General Help
---

### Post by AnotherMuggle on 2013-07-03
qtcreator is not showing anything on the examples tab.  Is there another package which I need to install to see the examples.  I am really interested in learning qt and the examples would be a massive help.  A basic install on Windows 7 automatically populates the examples tab and I'm hoping to achieve the same in Ubuntu.

Cheers,
AnotherMuggle

---

### Post by DeathByDenim on 2013-07-03
Strange, it definitely should. Those come from the package qt4-demos.
That should be a dependency for qtcreator though and therefore already installed, but you might want to check.

---

### Post by AnotherMuggle on 2013-07-03
> **DeathByDenim said:**
> Strange, it definitely should. Those come from the package qt4-demos.
That should be a dependency for qtcreator though and therefore already installed, but you might want to check.

```
$ sudo dpkg -s qt4-demos
dpkg-query: package 'qt4-demos' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,

```

The qt version installed is 5.0.1.

This issue seems to affect Mageia 3 aswell so I'm not sure where to start looking.

---

### Post by AnotherMuggle on 2013-07-07
> **AnotherMuggle said:**
> ```
$ sudo dpkg -s qt4-demos
dpkg-query: package 'qt4-demos' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,

```

The qt version installed is 5.0.1.

This issue seems to affect Mageia 3 aswell so I'm not sure where to start looking.

My "solution" was to uninstall the version from the Ubuntu repos and download and manually install from the Qt website.

Not my preferred way of installing software but it works perfectly now.

---

