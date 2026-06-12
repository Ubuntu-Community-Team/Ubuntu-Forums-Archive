---
title: "Boot Issue"
date: 2013-05-29
forum: General Help
---

### Post by Pyratsteve on 2013-05-29
Hi,

An odd boot issue started today.  I'm unable to boot without going in via recovery and then simply selecting 'continue in Normal mode' does the trick.  I've run  boot repair but to no avail.  Any tips?

[http://paste.ubuntu.com/5712845/](http://paste.ubuntu.com/5712845/)

---

### Post by Pyratsteve on 2013-06-10
bump

---

### Post by Bashing-om on 2013-06-10
[COLOR=#000000]Pyratsteve; Hi !

There just is not much to respond to... when you lost the ability to boot ...what had transpired ?
What pops to mind is that an update broke your proprietary graphics driver (maybe ?).
[/COLOR]To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```
[INDENT=2]only a shot in the dark

[/INDENT]

---

