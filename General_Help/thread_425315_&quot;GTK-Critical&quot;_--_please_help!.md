---
title: "&quot;GTK-Critical&quot; -- please help!"
date: 2007-04-27
forum: General Help
---

### Post by Flaringo on 2007-04-27
Lately I've been getting a lot of these errors: 

```
(synaptic:32272): Gtk-CRITICAL **: gtk_tree_view_unref_tree_helper: assertion `node != NULL' failed
```

Everything works, but I keep getting those errors (all "labeled" Gtk-CRITICAL). I have no idea what's wrong and how to fix it, and I hate the thought of that something's wrong. :sad:

---

### Post by Flaringo on 2007-04-27
Anyone? :-\

---

### Post by kevinsun on 2007-07-30
same here.... again, no solution.  I don't know, I having fontconfig error, too.

:confused:

Kevin.

---

### Post by AlexThomson_NZ on 2007-07-30
That looks to me like:
a) sloppy programming (not checking for a null before unreferencing)
or
b) possible changes to gtk+ between versions introducing error/warnings

Probably a mixture of both.  Definitely 100% worth pointing out to the maintainer of the app in question (usually an easy fix)

---

### Post by kevinsun on 2007-07-31
> **kevinsun said:**
> same here.... again, no solution.  I don't know, I having fontconfig error, too.

:confused:

Kevin.

I found that it's somewhere related to the theme cause when I chose different theme (namely the normal one like human), the error messages reduced and the hanging problem wasn't that serious.

Kevin.

---

