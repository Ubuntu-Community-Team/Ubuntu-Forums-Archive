---
title: "What is a &quot;recommended dependency&quot;?"
date: 2013-10-28
forum: General Help
---

### Post by vasa1 on 2013-10-28
In [this post]("http://ubuntuforums.org/showthread.php?t=2184003&p=12830475#post12830475"), there is mention of a *recommended dependency*. I thought that *recommends* and *dependencies* were different: I understood a dependency as something that a package requires and that installation of the package would not be (normally) possible without installing (automatically) the dependency as well.

I also think that apt-get, by default, installs recommends as well as the mandatory dependencies but that the installation of recommends can be prevented by --no-install-recommends. (IIRC, Synaptic also installs recommends by defaults but there's a GUI option to turn that off.)

---

### Post by mc4man on 2013-10-28
[http://www.debian.org/doc/debian-policy/ch-relationships.html](http://www.debian.org/doc/debian-policy/ch-relationships.html)
(7.2

---

### Post by vasa1 on 2013-10-28
> **mc4man said:**
> [http://www.debian.org/doc/debian-policy/ch-relationships.html](http://www.debian.org/doc/debian-policy/ch-relationships.html)
(7.2
From there:

> 
Recommends

    This declares a strong, but not absolute, dependency.

    The Recommends field should list packages that would be found together with this one in all but unusual installations.



---

