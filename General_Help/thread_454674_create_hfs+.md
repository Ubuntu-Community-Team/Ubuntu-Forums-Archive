---
title: "create hfs+"
date: 2007-05-25
forum: General Help
---

### Post by Wofl on 2007-05-25
hey guys...

i was wondering what i need to do in order to be able to create hfs+ partitions...

o can make hfs, but not hfs+

i already installed hfsutils, but no luck so far

---

### Post by Wofl on 2007-05-26
i looked around, and i am apparently able to resize now, but creating still not possible...

---

### Post by ruy_lopez on 2007-05-26
hfs support is experimental. You can read from hfs/+ drives, and there are tools that will write to them, but creating them isn't a trivial operation. If you are looking for a way to share a drive with Mac OS X, there is a ext2/3 extension for the preference pane, that will mount ext2/3 drives on OS X.

Creating HFS+ partitions involves patching your kernel.

[http://gentoo-wiki.com/HOWTO_hfsplus](http://gentoo-wiki.com/HOWTO_hfsplus)

---

