---
title: "how to install kile 2.01"
date: 2008-05-19
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-05-19
i've just downloaded the newest version of kile here:
[http://kile.sourceforge.net/download.php](http://kile.sourceforge.net/download.php)
how to install it? sorry for my n00bish question! :( thanks!

---

### Post by tzulberti on 2008-05-20
The repositories already have kile. You should install it using "sudo apt-get install kile". If you want a graphic point instead of console, use Synaptic (System -> Administration -> Synaptic Package Manager)

The short story is this: you have downloaded the kile code so to install it you have to compile which isn't very easy. Ubuntu uses a system called dpkg that has in a server a lot of programs (something like 20.000) already compiled, so you should only use the command apt (or Synaptic) and install it. The deb packages should be something like the *.exe in Windows.

---

### Post by afeasfaerw23231233 on 2008-05-22
but kile 2.01 is not in the repositories. it's  kile-i18n . i want the newest version because it enables inline preview of latex math equation.

---

### Post by dvase on 2008-05-22
> **afeasfaerw23231233 said:**
> but kile 2.01 is not in the repositories. it's  kile-i18n . i want the newest version because it enables inline preview of latex math equation.

Kile 2.01 is in the Hardy repositories.  You can [compile]("http://kile.sourceforge.net/help.php#compile") the version from the SourceForge website.  However, if I recall correctly from the last time I did so, there are a number of KDE development environment dependencies.  You might be better off biting the bullet and installing Hardy.

---

