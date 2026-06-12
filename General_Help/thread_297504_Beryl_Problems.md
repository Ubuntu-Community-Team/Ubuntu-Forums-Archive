---
title: "Beryl Problems"
date: 2006-11-11
forum: General Help
---

### Post by PPAAUULL on 2006-11-11
I have just installed beryl on my Ubuntu edgy computer. I am using a ATI 9200PRO card and the opensource driver for AIGLX but I have a problem starting and running beryl. I do have 3d acceleration and have checked that many times. What happens is that every time I start beryl the system starts to load it then freezes for about 3 seconds then just goes back to the login screen. Does anyone know of this problem and/or how to fix it? Thanks for the help.

---

### Post by qscgz on 2006-11-11
Google search:

ATI 9200 beryl site:ubuntuforums.org

[https://wiki.ubuntu.com/FindPage](https://wiki.ubuntu.com/FindPage)

Hopefully this gives you a glue?

---

### Post by jordanmthomas on 2006-11-11
Try this:
```
beryl-start > error.txt
```
It will kick you off as usual, and when you log back in you should be able to see the errors that happened to beryl-start in a file called error.txt

Also, look in /var/log at your X error messages for some hints.

---

