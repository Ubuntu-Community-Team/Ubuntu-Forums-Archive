---
title: "[SOLVED] Cache in System Monitor Applet"
date: 2008-04-19
forum: General Help
---

### Post by george9233 on 2008-04-19
Hi. I've got the system monitor added to my gnome panel. By the time I start the computer, both the memory and cache usage is very low. However, as time passes by, the cache starts to grow. When my cursor is hovering upon it, it says 

"Memory: 
27% in use by programs
66% in use as cache"

Do you know how this cache is formed, what is it for, and is there anyway I can flush it?

Thanks very much.

---

### Post by ryanhaigh on 2008-04-19
This page may explain things a little, in summary cache=good.
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

### Post by prshah on 2008-04-19
> **george9233 said:**
> 
"Memory: 
27% in use by programs
66% in use as cache"


Every operating system uses spare memory as cache, only not so transparently as in ubuntu. As and when your programs and data need more memory, the cache is automatically released. As the previous poster has said> cache=good

Nothing to worry about or do about.

---

### Post by george9233 on 2008-04-20
Thanks very much. All very useful information.

---

