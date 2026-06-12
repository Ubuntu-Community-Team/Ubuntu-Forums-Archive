---
title: "File System options"
date: 2007-06-03
forum: General Help
---

### Post by x1a4 on 2007-06-03
Hi,

I need some detailed info regarding the following file system options.

**sync vs async**
What exactly does it mean if a FS is accessed synchronously and asynchronously?  Which is better?

**mand vs nomand**
What is file system locking?

**encryption and loop**

---

### Post by kidders on 2007-06-04
Hi there,

> **x1a4 said:**
> I need some detailed info regarding the following file system options.The words you mentioned look like mount options ... the best thing to do would be to read a few discussions on the topic.

**sync vs async**
These options control when I/O buffers are flushed. Neither is better ... they're just different. The "sync" mount option is most often used for volatile, networked or floppy devices.

**mand vs nomand**
These options control access to files that may be in use. They are rarely used, and I wouldn't advise playing with them, unless you really know what you're doing.

**encryption and loop**
These options don't have much to do with each other (except that they often appear together in the same command). The "loop" option forces the kernel to mount a filesystem (typically something wrapped in another filesystem, eg an ISO image) using a loopback device. The "encryption" option lets you specify what encryption algorithm to use.

Hopefully that helps a little.

[[SIZE=1][COLOR=Silver]UAResolved[/COLOR][/SIZE]]("http://ubuntuforums.org/showthread.php?t=377083")

---

