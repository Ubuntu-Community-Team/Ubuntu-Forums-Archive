---
title: "&quot;Make Link&quot; problem"
date: 2007-02-04
forum: General Help
---

### Post by Graham1 on 2007-02-04
Hi 

Please help :). I've used the "Make Link" to link to my data drive and copied to my desktop (I now have two links). How can I remove these?

:)

---

### Post by taurus on 2007-02-04
You can use the "rm" command for a file or "rmdir" for a directory from a terminal.

```
rm **filename**
-or-
rmdir **directory**
```

---

### Post by Graham1 on 2007-02-04
I won't loose any data though? (on my data partition). Are these just shortcuts?

:)

---

### Post by taurus on 2007-02-04
You only remove the link so the original partition is still there.

For instance, if I link /home/taurus/doc to /home/taurus/personal/doc, I would run

```
ln -s /home/taurus/personal/doc /home/taurus/doc
```
And if I want to remove /home/taurus/doc, I would then do

```
rmdir /home/taurus/doc
```
and /home/taurus/personal/doc is still there.

---

### Post by Graham1 on 2007-02-04
Both now removed. Thanks for your help.

:)

---

