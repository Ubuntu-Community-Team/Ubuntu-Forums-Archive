---
title: "Remove item from APT list"
date: 2013-01-22
forum: General Help
---

### Post by mrphud on 2013-01-22
Hi there,

I was reinstalling google earth today because all the icons in the properties folder disappeard for some reason. When I went to uninstall and reinstall I noticed that there was a file "googleearth" under APT. However, the active package is something like google-earth-stable. I tried to install the googlearth option but got this

```
Package googleearth is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'googleearth' has no installation candidate
```

Does anyone know why this is? How can I remove the googleearth option if it is obselete. Furthmore, how can I do a sweep of all obselete packages on my computer?

Cheers

---

### Post by ibjsb4 on 2013-01-22
> Furthmore, how can I do a sweep of all obselete packages on my computer?


One way is in terminal.

```
sudo apt-get autoremove
```[https://help.ubuntu.com/community/AptGet/Howto#Removal_commands](https://help.ubuntu.com/community/AptGet/Howto#Removal_commands)

I think a better way is BleachBit, its in the software center.  Just take a minute and be sure about what all you want cleaned.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

