---
title: "No access to pipe for printing in Mousepad."
date: 2007-01-12
forum: General Help
---

### Post by phossal on 2007-01-12
I read somewhere, perhaps in the package manager, that mousepad was created on top of leafpad (which I love) to offer printing support.

When I try to print, I get:
> Can't open pipe to process.
What am I doing wrong?

---

### Post by tweedledee on 2007-01-13
> **phossal said:**
> I read somewhere, perhaps in the package manager, that mousepad was created on top of leafpad (which I love) to offer printing support.

When I try to print, I get:

What am I doing wrong?

Interesting.  I'd installed mousepad for the same reason, and thought I'd tested printing, but perhaps not; when I try it now, I get the same error.  Looks like a bug report should be filed, if it doesn't already exist (you should search the Launchpad site, available via Bug Reports via the Wiki).

---

### Post by phossal on 2007-04-13
Has anyone figured out why mousepad won't print?

---

### Post by phossal on 2007-04-13
I realize, now, that printing has dependencies. First off, you have to:
```
sudo apt-get install mousepad
sudo apt-get install xfprint4
sudo apt-get install a2ps
```

However, now I'm confronted with a new error message from the print dialog box:
```
** (xfprint4:5740): CRITICAL **: printing_system_get_printers: assertion `ps' failed

** (xfprint4:5740): CRITICAL **: printing_system_get_default_printer: assertion `ps' failed

(xfprint4:5740): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
[/dev/stdin (plain): 1 page on 1 sheet]
[Total: 1 page on 1 sheet] sent to the standard output

```

---

### Post by phossal on 2007-04-13
I've read after 40 minutes of searching that cups has a backend that can be enabled to allow printing from xfprint. I know how to access the cups admin page, but I have no idea how to configure this. Does anyone know how to do anything complicated in this perpetually broken OS? Windows prints slowly, but it *does* print from notepad.

If not, I'm giving up on Ubuntu. You can only install Java and Beryl so many times before you realize you have work to do.

---

