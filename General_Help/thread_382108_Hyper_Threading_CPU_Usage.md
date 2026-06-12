---
title: "Hyper Threading CPU Usage"
date: 2007-03-11
forum: General Help
---

### Post by GMWeezel on 2007-03-11
My computer has hyper threading and I have the i686 kernel with SMP installed but some applications only use %50 of my processor. Do I need to recompile the programs for my kernel?

---

### Post by russell.h on 2007-03-11
Most likely the programs are single threaded. I'm not sure about "hyper threading", but thats how it is with dual core processors. You would need to actually rewrite the program, not just recompile it.

---

