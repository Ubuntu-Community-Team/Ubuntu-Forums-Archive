---
title: "I have no /usr/src/linux link...?"
date: 2006-10-31
forum: General Help
---

### Post by kcy29581 on 2006-10-31
Hi all,

I have just noticed that my /usr/src folder has no "linux" symbolic link (see attached image).

Is this correct? I thought you ALWAYS had to have a /usr/src/linux folder (link)?

Or is this something Ubuntu does differently?

Thnaks for any help.

---

### Post by fguilhon on 2006-10-31
No. You don't have to HAVE the symlink. 
It's good to have when you are compiling a new kernel, when in this case, you make the symlink(/usr/src/linux) to the linux sources you want to compile.

---

### Post by kcy29581 on 2006-10-31
> **fguilhon said:**
> No. You don't have to HAVE the symlink. 
It's good to have when you are compiling a new kernel, when in this case, you make the symlink(/usr/src/linux) to the linux sources you want to compile.
thanks for the speedy reply. I'll make it myself then :)

---

