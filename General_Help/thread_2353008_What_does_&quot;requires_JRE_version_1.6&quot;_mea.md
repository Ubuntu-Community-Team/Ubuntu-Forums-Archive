---
title: "What does &quot;requires JRE version 1.6&quot; mean?"
date: 2017-02-17
forum: General Help
---

### Post by dora5 on 2017-02-17
If the current version of Heritrix "requires JRE 1.6", does that mean it requires ATLEAST version 1.6, or EXACTLY version 1.6?   

What is the best thing to do if I have the later version on my computer and want to keep it?  Everything else wants the up to date version.  Is it possible to have more than one version of the JRE installed in Ubuntu?

Yours,
Dora Smith

---

### Post by QIII on 2017-02-17
Yes, you can have more than one version of the JRE installed.  You can switch between them.

But to be perfectly frank, I would *absolutely not use anything that calls only for 6*.  That version was riddled with security holes and has not been updated in years.  Even Oracle says not to use it.  Java 6 was responsible for the October of Exploits a few years ago.  At that time Red Hat broadcast a message to its customers to completely uninstall Oracle Java.

---

