---
title: "how to enable c development man pages"
date: 2005-04-26
forum: General Help
---

### Post by cjm on 2005-04-26
i want to type man fprint etc and get the man pages for c development.

i have installed:

glibc-doc
manpages-dev

but still get no response.  can anyone help?

thanks in advance.

---

### Post by ape on 2005-04-27
If you do a `man fprintf`, you will get a man page that covers fprint.  This seems to come from the manpages-dev package.  To see what functions are part of this package, issue the command `dpkg -L manpages-dev | more` in a shell.

---

### Post by cjm on 2005-05-02
thanks for that bit of advice.... all has been sorted now

cheers

---

