---
title: "How to set the TOPDIR variable"
date: 2006-11-25
forum: General Help
---

### Post by Nickb-k on 2006-11-25
Hello,

I'm trying to compile a program that requires the TOPDIR environmental variable to be set.  Trying the ususal:

```


# TOPDIR = /usr/src/ogdi-3.1.5/
  bash: TOPDIR: command not found

```

And ```
echo $TOPDIR
``` returns nothing.  I have tried adding a line to /etc/environment but that didnt help either.

How can I add the TOPDIR variable to my machine?

Thanks in advance,

Nick

---

### Post by taurus on 2006-11-25
What are you trying to compile anyway?  Try to add that to your ~/.bashrc and "source" it...

```
source ~/.bashrc
```

---

### Post by Nickb-k on 2006-11-25
Thank you - it worked.

I am compiling the [OGDI]("http://ogdi.sourceforge.net/") library.

Thank gain :)

---

### Post by taurus on 2006-11-25
> **Nickb-k said:**
> Thank you - it worked.

I am compiling the [OGDI]("http://ogdi.sourceforge.net/") library.

Thank gain :)
Glad to help.

---

