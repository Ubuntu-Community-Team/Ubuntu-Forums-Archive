---
title: "automatix and gmail-notify"
date: 2006-07-07
forum: General Help
---

### Post by christian on 2006-07-07
I've installed and run automatix... it seems to have installed gmail-notify (when i search files in nautilus, it's there!) but i can't find anyway of actually getting gmail-notify to run...? does anyone know how to do this?

thanks!

---

### Post by jongkind on 2006-07-07
As first step I suggest to verify whether gmail-notify indeed is installed. If not, you can install it via Synaptic.

To start gmail-notify automatically you can add it to system-preferences-sessions-Startup programs and use gmail-notify as command.

Good luck

---

### Post by christian on 2006-07-07
thanks- i've put it in my startup menu. Also tried running it from a terminal which worked fine.


... i've also just noticed that after running it in a terminal that it's appeared in my applications list. Problem sorted- cheers!

---

### Post by arnieboy on 2006-07-07
> **christian said:**
> I've installed and run automatix... it seems to have installed gmail-notify (when i search files in nautilus, it's there!) but i can't find anyway of actually getting gmail-notify to run...? does anyone know how to do this?

thanks!

Automatix installs checkgmail (NOT gmail-notify) which in my opinion is much better than gmail-notify. There is no menu entry for checkgmail (maybe something which the package maintainers need to look into)

To run checkgmail the first time run it from terminal as follows:
```
checkgmail
```
After you configure it, add it to the startup programs.

---

### Post by christian on 2006-07-07
thanks- yeah it looks better- though i don't know how i got gmail-notify on here then (is it preinstalled with dapper?)

---

### Post by arnieboy on 2006-07-07
> **christian said:**
> thanks- yeah it looks better- though i don't know how i got gmail-notify on here then (is it preinstalled with dapper?)

not sure.. you can remove it from synpatic if you want.

---

