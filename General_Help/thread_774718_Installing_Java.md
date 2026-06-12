---
title: "Installing Java"
date: 2008-04-29
forum: General Help
---

### Post by the.fubz on 2008-04-29
How do you install Java JRE in Ubuntu?

---

### Post by Abandon on 2008-04-29
> **the.fubz said:**
> How do you install Java JRE in Ubuntu?

The answer for that question (and more) can be found here:

[http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html](http://linuxondesktop.blogspot.com/2008/04/things-to-do-on-your-new-ubuntu-804.html)

---

### Post by ivze on 2008-04-29
See sun-java6-jre Synaptic package. Search for sun-java in Synaptic - it gives much entries.

---

### Post by the.fubz on 2008-04-29
> **ivze said:**
> See sun-java6-jre Synaptic package. Search for sun-java in Synaptic - it gives much entries.

Thanks, that helped me find it; however, when I try to open an applet in firefox it still does not load.

Now what?

---

### Post by Abandon on 2008-04-29
> **the.fubz said:**
> Thanks, that helped me find it; however, when I try to open an applet in firefox it still does not load.

Now what?

From a terminal:

sudo update-alternatives --config java 

and choose the other version.

---

### Post by the.fubz on 2008-04-29
> **Abandon said:**
> From a terminal:

sudo update-alternatives --config java 

and choose the other version.

Thanks, it works now :)

---

