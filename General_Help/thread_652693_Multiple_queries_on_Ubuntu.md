---
title: "Multiple queries on Ubuntu"
date: 2007-12-29
forum: General Help
---

### Post by karthik_jce on 2007-12-29
Hi,

    I have the following queries with Ubuntu,

1. Can we install KDE(kubunut) applications on ubuntu
2. When I install applications with synaptic pakage manager, were are these getting installed. Is it under root "/" directory ?
3. If so is it possible to install these on some other location.

Regards
Karthigeyan

---

### Post by PeterJS on 2007-12-29
> **karthik_jce said:**
> Hi,

    I have the following queries with Ubuntu,

1. Can we install KDE(kubunut) applications on ubuntu

Yeah, go for it, but know that the different desktop environments use different theming engines so the applications won't look the same unless you can find matching themes. Also Gnome has a bunch of components pre-installed so for it's apps you will only need the program itself, but until you've build a critical mass of equivalent KDE components they will take more disk space to install.
> 
2. When I install applications with synaptic pakage manager, were are these getting installed. Is it under root "/" directory ?
Here's the wikipedia article on what goes where:
[http://en.wikipedia.org/wiki//etc#Directory_structure](http://en.wikipedia.org/wiki//etc#Directory_structure)
> 
3. If so is it possible to install these on some other location.
Yes this is possible, but a *very* bad idea. Windows is built on the idea that each application manages all of it own components, linux doesn't work like that, in linux the OS manages whats installed, and each program tells the OS what components it needs when it's installed, and the system makes sure they're their, if you put things in non-standard locations the OS can't find them, and you'll end up with duplicates or things broken.

---

