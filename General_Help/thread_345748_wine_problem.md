---
title: "wine problem"
date: 2007-01-24
forum: General Help
---

### Post by joe56 on 2007-01-24
i'm trying to run an .exe file in wine but when i run the command this is all i get

fixme:seh:set_cpu_context setting partial context (13) not supported
fixme:seh:set_cpu_context setting partial context (13) not supported
fixme:seh:set_cpu_context setting partial context (13) not supported
...
repeated many times
...
err:seh:setup_exception stack overflow 680 bytes in thread 0009 eip b7d53dc3 esp 00230d58 stack 0x231000-0x340000
joe@joe-desktop:~$ 

any suggestions?

---

### Post by scrooge_74 on 2007-01-24
seems your .exe program is not supported, if it is a known program you can check on [winehq]("http://www.winehq.org") database to see if it is supported

---

### Post by machoo02 on 2007-01-24
What program are you trying to run?

---

