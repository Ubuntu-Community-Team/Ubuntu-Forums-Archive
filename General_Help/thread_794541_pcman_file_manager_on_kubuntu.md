---
title: "pcman file manager on kubuntu"
date: 2008-05-14
forum: General Help
---

### Post by bone2006 on 2008-05-14
I've been having problems installing pcman file manager on kubuntu.   It complains about gtk+icon theme not properly installed.  I've tried a few things, but can't seem to get it to work in kubuntu.
Any help?

---

### Post by eriqjaffe on 2008-05-15
Just add something like this:

```
gtk-icon-theme-name="Tango"
```

to your ~/.gtkrc-2.0 file.  If you don't have that file, just create it.

Obviously, you'd need to install the Tango icon set to use that specific line - it's in the repos.

---

