---
title: "Is possible &quot;make&quot; using an default for compile if is gcc12 and  kernel is gcc 9 ?"
date: 2024-01-07
forum: General Help
---

### Post by aug7744 on 2024-01-07
Hello.
Thanks for reading my topic.

Ubuntu 20.04.6 with kernel 6.6.5 and gcc 12.3
However the kernel was compiled using gcc 9.
When is used command "make" happen errors warnings and not is possible complete compilation for some softwares.
Need add in command "HOSTCC=gcc-12 CC=gcc-12"
make HOSTCC=gcc-12 CC=gcc-12

Is possible compile without errors and the software works corretly.
The problem is when some software in deb file format does internally an make command for example Virtual Box.
Not is possible complete installation.

Is possible configure an default for when using make to use "HOSTCC=gcc-12 CC=gcc-12" in all commands ?

Have an nice week.

---

### Post by MAFoElffen on 2024-01-07
I'm thinking maybe this might help with that: [https://www.reddit.com/r/virtualbox/comments/zidjkd/comment/izsevkr/?utm_source=share&utm_medium=web2x&context=3](https://www.reddit.com/r/virtualbox/comments/zidjkd/comment/izsevkr/?utm_source=share&utm_medium=web2x&context=3)

If not in itself, then maybe one of the other suggestions there... Seems to sound very similar to what you seem to be trying to do.

---

