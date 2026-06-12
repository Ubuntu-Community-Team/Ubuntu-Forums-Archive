---
title: "how do i see which packages are availbile in a certain repo?"
date: 2006-12-26
forum: General Help
---

### Post by ewaguespack on 2006-12-26
i was looking here...

[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

and i wanted to check out the packages available in the repositories that are listed.

is there a way to do this? basically do an apt-cache search --repo=bla or something?


thanks.

---

### Post by bruenig on 2006-12-26
To browse the repositories, you can just open them up in a browser.

For instance, the repository listed as
```
deb http://kubuntu.org/packages/kde-latest edgy main
```

Just go to [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest)

---

### Post by mexlinux on 2006-12-26
Ignore.
(Just bookmarking)

---

### Post by ewaguespack on 2006-12-26
well the website does not appear to always list the packages on their website, specifically the canonical and the plf... (the latter may not support edgy, not sure)

# Penguin Liberation Front (packages)

deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) edgy-plf free non-free

# Canonical Commercial Repository (Opera,Real Player10.. etc)

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

---

### Post by ewaguespack on 2006-12-26
nevermind i guess, i found a work around, but i may as well just go to /var/lib/apt or whatever and do it manually.

[http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/dapper-commercial/main/binary-i386/Packages.gz)

---

