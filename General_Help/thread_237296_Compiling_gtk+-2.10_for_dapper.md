---
title: "Compiling gtk+-2.10 for dapper"
date: 2006-08-15
forum: General Help
---

### Post by hanzomon4 on 2006-08-15
I trying to get gtk to compile, configure goes fine but make fails with this error
```
collect2: ld returned 1 exit status
make[4]: *** [gtk-query-immodules-2.0] Error 1
make[4]: Leaving directory `/root/src/gtk+-2.10.0/gtk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/src/gtk+-2.10.0/gtk'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/src/gtk+-2.10.0/gtk'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/src/gtk+-2.10.0'
make: *** [all] Error 2
```
I have glib 2.12.1 installed and I have checked to make sure that I had all dependences meet, and like I said configure gives no errors. how do attach files?  I want to post the config.log if it'll help

---

### Post by simonn on 2006-08-16
Why are you install gtk 2.10?

---

### Post by hanzomon4 on 2006-08-16
I'm installing to get my window types working in compiz again
[quote=moppsy]
Turns out that gtk+ needed upgrading.
2.10 has the new window types.
[/quote]

---

### Post by hanzomon4 on 2006-08-16
Got it I had to ./configure glib 2.12.1 with the --prefix=/usr option

---

