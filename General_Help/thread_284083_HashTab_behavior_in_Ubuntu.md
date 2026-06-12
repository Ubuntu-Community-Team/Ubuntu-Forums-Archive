---
title: "HashTab behavior in Ubuntu"
date: 2006-10-25
forum: General Help
---

### Post by williamts99 on 2006-10-25
I don't know if anyone has seen [HashTab]("http://www.beeblebrox.org/hashtab/") for Windows, but it is great for quickly checking the hash of a file.  How would we get something like this implemented in Ubuntu?  It would be really nice to be able to right click on a file to check the properties, and have a hashes tab.  For example, what package would it be, and where would you request something like this?  Would it be better as a separate package or integrated into Gnome?  What do you guys think?

---

### Post by po0f on 2006-10-25
williamts99,

A combination of [nautilus-actions](http://packages.ubuntu.com/dapper/gnome/nautilus-actions) and md5sum will probably do the trick.

---

