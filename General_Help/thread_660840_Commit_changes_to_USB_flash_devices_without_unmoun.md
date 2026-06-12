---
title: "Commit changes to USB flash devices without unmounting?"
date: 2008-01-07
forum: General Help
---

### Post by kcy29581 on 2008-01-07
Hi all,

When I copy files to external USB flash drives (using nautilus), I understand that the actions are not committed to the devices until I unmount them.

Is there a way to have the changes committed to the devices without having to mount/unmount, command-line or graphical?

Thanks

---

### Post by heindsight on 2008-01-07
You can use the sync command.
Have a look at
```
man sync
```
and
```
info coreutils sync
```
for details on how it works.

---

### Post by kcy29581 on 2008-01-07
heindsight, you are a legend :).

Such a simple, obvious little command! The beauty of Linux!

---

