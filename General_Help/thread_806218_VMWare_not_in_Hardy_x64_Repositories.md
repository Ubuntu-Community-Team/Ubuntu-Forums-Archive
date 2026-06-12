---
title: "VMWare not in Hardy x64 Repositories?"
date: 2008-05-24
forum: General Help
---

### Post by jacoblyles on 2008-05-24
When I try to install the vmware-server package, I get the error: 

```
E: Couldn't find package vmware-server

```

Here's my sources.list. Any problems?

```

deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner
deb http://archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ hardy-updates universe main multiverse restricted

```

---

### Post by tmak on 2008-06-20
I have no solution for this but i can confirm this. There isn't even a package for 32bit yet. I'm currently waiting for the release of these packages too because i have to setup some machines and don't want to install vmware-server by hand because of the breakage if a new kernel gets installed.

We'll just have to wait i suppose. There is a discussion on launchpad about this but there were no news on this matter for some weeks now.

---

