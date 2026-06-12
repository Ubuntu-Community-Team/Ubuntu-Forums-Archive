---
title: "Debian help"
date: 2008-01-22
forum: General Help
---

### Post by EYEdROP on 2008-01-22
Hello everyone. I am new to debian 4 coming from ubuntu, and I really like it. Im trying to get NTFS read/write support, but im running into issues. The dependinces for ntfs-3g are installed, but too early of a version for ntfs-3g to install. It seems like all the packages in debian are old and outdated. How can I get up to date packages like ubuntu? Are there any repositories I should add

---

### Post by EYEdROP on 2008-01-22
bump

---

### Post by wolfen69 on 2008-01-22
you're in the wrong forum, but here's how i did it. [http://technowizah.com/2006/11/debian-how-to-writing-to-ntfs.html](http://technowizah.com/2006/11/debian-how-to-writing-to-ntfs.html)

and don't expect an ntfs partition to automount in debian. that's a whole other thing.

---

### Post by pointone on 2008-01-23
You could upgrade from Debian stable (Etch) to Debian testing (Lenny) by editing /etc/apt/sources.list and changing all occurances of stable/etch to testing/lenny, then run:

```
apt-get dist-upgrade
```

This will upgrade your system to the Debian testing repository which has much more up-to-date packages. (Ubuntu uses Debian testing as a base.) I've never seen a need to run Debian stable unless it's a server or other sensitive system. Debian testing is essentially rock solid and provides a lot more usability for the average desktop user.

---

