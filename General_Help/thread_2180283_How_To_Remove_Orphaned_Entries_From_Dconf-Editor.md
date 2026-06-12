---
title: "How To Remove Orphaned Entries From Dconf-Editor?"
date: 2013-10-12
forum: General Help
---

### Post by buzzingrobot on 2013-10-12
How do you remove orphaned entries from the hierarchy displayed in the left panel of dconf-editor?

E.g., installing something often adds entries there.  Those entries persist after that "something" is removed.

---

### Post by ibjsb4 on 2013-10-12
I have not notice this behavior.  Do you --purge when removing packages?  Can you give us a package example that we can try?

---

### Post by steeldriver on 2013-10-12
I think you can use dconf reset, e.g.

```

$ dconf list /apps/
ubuntu-tweak/
$ 
$ dconf dump /apps/ > dconf.apps.orig

```

```

$ sudo apt-get purge ubuntu-tweak
Reading package lists... Done
.
.
.
Removing ubuntu-tweak ...
Purging configuration files for ubuntu-tweak ...
.
.
.
$ 
$ dconf list /apps/
ubuntu-tweak/

```

(still there); then

```

$ dconf reset -f /apps/ubuntu-tweak/
$ dconf list /apps/
$ 

```

(gone) - let's confirm by diffing the dumps

```

$ dconf dump /apps/ > dconf.apps.reset
$ diff dconf.apps.orig dconf.apps.reset
1,3d0
< 
< [ubuntu-tweak/janitor]
< janitor-view-width=235

```

**Be careful to only reset the schema paths you are trying to remove NOT the parent**

---

