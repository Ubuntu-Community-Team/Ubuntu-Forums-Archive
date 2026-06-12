---
title: "read only file system"
date: 2024-05-03
forum: General Help
---

### Post by lroy0 on 2024-05-03
Hello all,
I have a problem with permissions to do a task that I would perform. 
My problem is that one : I'm trying to copy a file "bepo.kl" into a directory read-only file system  : /var/lib/waydroid/rootfs/system/usr/keylayout
(It is a keybord layout for me to use in the application waydroid)
I have tried as root but it returns that it is a read only file system. So I don't know how to resolve it. 
Maybe you could explain me how to. 
Thank's in advance, 
Best regards

---

### Post by vanadium on 2024-05-03
Under 'var/lib/waydroid/rootfs/', the software mounts a file system contained in an image files. Such file systems are read-only. You may need to consult the documentation of the software, or ask on their forums, about how you should solve the problem you have.

---

### Post by btindie on 2024-05-03
A basic google search brings up [https://github.com/waydroid/waydroid/issues/599](https://github.com/waydroid/waydroid/issues/599) which should answer your question.

---

