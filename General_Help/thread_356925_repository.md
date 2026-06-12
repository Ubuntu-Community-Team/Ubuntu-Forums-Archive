---
title: "repository"
date: 2007-02-09
forum: General Help
---

### Post by chamath on 2007-02-09
Hi ...
 why  we make repositories.
chamath

---

### Post by finer recliner on 2007-02-09
repositories are a single location to easily update lots of linux applicatsions at once. it's just very convenient

---

### Post by chamath on 2007-02-09
can i add tar.gz files on it. or only .deb. How can we create it?

---

### Post by lukew on 2007-02-09
You can make your own repos; need to contain deb files only.

You can add to other peoples repos your own deb files; if you have permission and they let you.

Can you explain a little more about what your needs are?

Basically repos are for convenience. They provide a group of similar based packages all in one place. Combined with apt-get you get one seamless interface to install just about everything you need. They also handle a packages dependencies ( packages a package requires to be installed for it to run ) when installing ( installs them for you).

I deal if you keep a bit list of what you install so when you next need to do it you can just apt-get insatll package 1 package 2 .... package 99999.

Luke

---

