---
title: "Seahorse Dapper Backport"
date: 2006-09-27
forum: General Help
---

### Post by SpEcIeS on 2006-09-27
In general this version, 0.9.3-0ubuntu5, seems to work, but when you try and encrypt a file in nautilus it errors, at least on my machine. So, the solution was to add Edgy's seahorse 0.9.5-1ubuntu2. Works perfectly now. ;) 

To install do the following:
```
[b]Add Edgy source repos (below)

mkdir seahorse && cd seahorse

sudo apt-get source seahorse

Remove Edgy repos

cd seahorse-0.9.5 && sudo dpkg-buildpackage -b -uc

install deb package  using sudo dpkg -i *.deb[/b]
```

Here are the repos for edgy:
```
[b]# Ubuntu Edgy
deb http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

# Ubuntu Edgy updates.
deb http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

# Ubuntu Edgy backports project
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

# Ubuntu Edgy security updates
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse[/b]
```

Try out some other packages the same way. Many of the edgy packages compile well into dapper. Some need some tweaking. Good luck. :D

---

### Post by JamesB on 2006-09-27
Hey, nice tip, gonna try with kaffine 0.8.1

---

