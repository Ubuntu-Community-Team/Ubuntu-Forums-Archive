---
title: "apt pinning question"
date: 2007-04-22
forum: General Help
---

### Post by banditti on 2007-04-22
This is what I want to do.  To install beryl under feisty, I need to use the repository from beryl-projects.org and not the one from universe.

What I want to do is to tell apt to only install/update beryl from the beryl repository and not the universe.  

I was looking at pinning, but they are both feisty repositories. 

What am I missing?

---

### Post by matthewdhandley on 2007-04-22
Can you just disable the universe source temporarily in Software sources?

---

### Post by banditti on 2007-04-22
which is what I did.  I can enable when complete and not worry about conflicts?

---

### Post by banditti on 2007-04-23
When I add universe back, it wants to update beryl.

There has to be a way around this.  Anyone?

---

### Post by robrmd9 on 2007-04-23
Hey,

I recently did this to keep my vnc4server as the edgy version and keep aptitude from upgrading it to the feisty one.

To pin a package, you have to create the file /etc/apt/preferences.  In the file, put something like:

```
Package: vnc4server
Pin: version 4.1.1+xorg1.0.2-0ubuntu1
Pin-Priority: 1000
```

This will keep the package at the specified version.

For more information, check this link:

[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html")

---

