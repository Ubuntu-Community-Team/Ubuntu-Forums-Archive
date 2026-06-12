---
title: "repo issues (internet related?)"
date: 2006-12-01
forum: General Help
---

### Post by lemonsCC on 2006-12-01
I am trying to install xterm on an ubunut(lite) box and I am having repo issues.  aptitude wants to uninstall ~400 packages (all of ubuntu-lite) apt-get says > failed to fetch [http://..blah..blah.deb](http://..blah..blah.deb)  temporary failure resolving us.archive.ubuntu.com......

I am thinking it may be an internet problem but dont know where to start as I am used to gnomes networking panels.

---

### Post by lemonsCC on 2006-12-01
```
sudo dhclient eth0
```

solved the problem

---

