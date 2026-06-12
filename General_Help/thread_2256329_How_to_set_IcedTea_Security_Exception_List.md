---
title: "How to set IcedTea Security Exception List"
date: 2014-12-11
forum: General Help
---

### Post by thewozza on 2014-12-11
It's easy on Windows with Oracle Java, you just go into the Java security settings and configure the exception list.

But I can't find it on OpenJDK Ubuntu.  The control panels just don't show anything marked "security exception list".

This is to make an unsigned jar run - it's required for me to do my job so I don't really have a choice with this.  Right now I'm loading a VM with Windows to continue working, but as you can imagine that's not nice.

---

### Post by nerdtron on 2014-12-11
On my system I have the Icedtea Web control panel. It will show settings regarding Java, including whitlisting

---

### Post by thewozza on 2014-12-11
I do have the Icedtea control panel, but it makes no mention of a white-list.

---

### Post by nerdtron on 2014-12-11
Is this the part where you put the website URL and set to always trust.
[ATTACH=CONFIG]258500[/ATTACH]

---

