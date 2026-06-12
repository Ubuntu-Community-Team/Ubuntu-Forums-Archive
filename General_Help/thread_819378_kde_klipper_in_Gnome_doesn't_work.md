---
title: "kde klipper in Gnome doesn't work"
date: 2008-06-05
forum: General Help
---

### Post by jtheb on 2008-06-05
I installed the kde klipper program and the install went fine.
However, the klipper app will not execute.  

Help appreciated.  this is a fine app for clipboard work

---

### Post by sizzam on 2008-06-05
Is there any output when you execute 'klipper' from a command line?

Also, there is an app in the repos called 'glipper', which is a GTK app that is similar to klipper.

```
$ sudo apt-get install glipper
```

Then, add it to your panel by right-clicking your panel, choosing 'Add to Panel', then selecting 'Clipboard Manager'.

---

### Post by jtheb on 2008-06-05
no output at the command line for klipper
installed glipper and it is in /usr/lib/glipper /usr/share/glipper but does not have a gui icon or run from the command line

acts like the install for klipper

---

### Post by sizzam on 2008-06-05
Glipper is an applet.  The gui icon is available via these steps:

Add it to your panel by right-clicking your panel, choosing 'Add to Panel', then selecting 'Clipboard Manager'.

---

### Post by jtheb on 2008-06-05
I didn't read the last line about control panel and it is there
Thank you very much
surprised Klipper didn't show up that way

---

### Post by jtheb on 2008-06-05
> **jtheb said:**
> no output at the command line for klipper
installed glipper and it is in /usr/lib/glipper /usr/share/glipper but does not have a gui icon or run from the command line

acts like the install for klipper


Output of glipper is strange
have you used it?

---

### Post by sizzam on 2008-06-05
Yep, I use it.  What strangeness are you seeing?

---

