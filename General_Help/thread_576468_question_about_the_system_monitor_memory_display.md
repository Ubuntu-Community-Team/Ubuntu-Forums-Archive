---
title: "question about the system monitor memory display"
date: 2007-10-15
forum: General Help
---

### Post by onesojourner on 2007-10-15
what does the it mean by the memory in cache? is that memory that you are not using? mine is always saying 50% in use by programs and 50% in use as cache. Am I using all my memory or am I using half?

---

### Post by Pumalite on 2007-10-15
Ubuntu will try to use all the memory you have and then page out.

---

### Post by az on 2007-10-15
> **onesojourner said:**
> what does the it mean by the memory in cache? is that memory that you are not using? mine is always saying 50% in use by programs and 50% in use as cache. Am I using all my memory or am I using half?

You are using your ram very efficiently.  If you did not cache things like shared libraries, your system would run extremely slowly.  The linux kernel is pretty good at deciding what to keep in ram (cache) and what to dump in favor of something new.  As a rule, you should use as much of your ram as possible at all times - this means that you will not clear the stuff in your cache until you absolutely need to.

---

