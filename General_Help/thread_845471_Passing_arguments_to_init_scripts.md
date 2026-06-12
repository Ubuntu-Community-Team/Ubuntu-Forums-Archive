---
title: "Passing arguments to init scripts?"
date: 2008-06-30
forum: General Help
---

### Post by Jc1991 on 2008-06-30
I've installed pure-ftpd via Synaptic, which creates a pure-ftpd service. I want to pass several arguments to the service on startup: how should I go about doing that?

---

### Post by justleen on 2008-06-30
good place to start would be the init script itself
eg. /etc/init.d/pure-ftpd

---

### Post by Jc1991 on 2008-06-30
While I (think I) understand the *concept* behind the init system, my understanding of the implementation is very limited: the only thing that I get out of reading the script is that there appears to be support for passing it a list of argument suffixes.

---

