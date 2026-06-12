---
title: "boot stuff not in /boot"
date: 2007-02-26
forum: General Help
---

### Post by retval on 2007-02-26
initrd.img, initrd.img.old, vmlinuz, vmlinuz.old are all in / and not /boot. Why?

---

### Post by tgalati4 on 2007-02-27
Welcome to the forums. 

Try 

ls -la

You should notice that they are in light blue color, meaning that they are symbolic links to the real location of the files, which is /boot.

Perhaps this is done for compatibility with certain compilers?  I really don't know.  Perhaps someonce could chime in. 

Try in a terminal:

man ln           (q to quit)

This will give you an appreciation of the link command.  It is useful for all sorts of unobvious things.

Of course a good way to learn linux is to break things.

Try in a root directory: (Warning, don't really do this.)

sudo unlink initrd.img 

and see what bad things happen.  That will give you a clue as to why it is set up that way.

Welcome to the forums.

---

