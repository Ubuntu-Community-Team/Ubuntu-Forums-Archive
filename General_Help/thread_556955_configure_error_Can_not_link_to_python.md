---
title: "configure: error: Can not link to python"
date: 2007-09-22
forum: General Help
---

### Post by fatfranko on 2007-09-22
im trying to install mod_python.  just wondering how to fix this error:

```

checking checking where python libraries are installed... /usr/lib/python2.5
checking for Py_NewInterpreter in -lpython2.5... no
configure: error: Can not link to python

```

---

### Post by fatfranko on 2007-09-22
*bump*

---

### Post by fatfranko on 2007-09-22
im kind of a newbie when it comes to forums.  should i repost this in the programming section or is reposts frowned upon?  i don't want to be hated...  im really cool... honest :)

---

### Post by schlauberg on 2007-12-01
Hi,

Quite often when you try to compile stuff on your own, you get more or less cryptic error messages.
In most cases you can resolve them if you install the developer versions of the base packages which
are need.

In your case "sudo aptitude install python-dev" should solve the problem.

---

