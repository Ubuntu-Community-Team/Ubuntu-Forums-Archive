---
title: "system info"
date: 2008-07-02
forum: General Help
---

### Post by gandalf458 on 2008-07-02
Is there somewhere I can find out the size of my hard disk, amount remaining, installed RAM and other system information?

---

### Post by StOoZ on 2008-07-02
take a look at :
> man lshw

and then use it

---

### Post by ibutho on 2008-07-02
You can several tools e.g. for the hard disk
```
df -h
```
For general sysinfo, you can use
```
lshw
```
and for pci devices use
```
lscpi
```
Each command has other options so read the manuals if you want to fine tune the output. If you prefer using GUI tools, then install gnome-device-manager or lshw-gtk.

---

### Post by ModelM on 2008-07-02
You could also try...

Select the "System" menu

Select "Administration"

Select "System Monitor"

---

### Post by gandalf458 on 2008-07-02
Thanks guys.

G :)

---

