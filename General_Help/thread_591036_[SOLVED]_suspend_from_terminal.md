---
title: "[SOLVED] suspend from terminal?"
date: 2007-10-25
forum: General Help
---

### Post by stinkinrich88 on 2007-10-25
hello, how do I suspend my computer by running a command e.g. in the terminal?

thanks!!

---

### Post by Zackariah on 2007-10-25
You could try > apmsleep

---

### Post by stinkinrich88 on 2007-10-25
> **Zackariah said:**
> You could try

hey, thanks, but I get

> apmsleep: Your kernel does not support APM.
apmsleep: Recompile kernel with APM and /dev/rtc support

also it wants me to specify how long i want to suspend for. I want it indefinite. 

Thanks!

---

### Post by nick_h on 2007-10-25
The script you need to run is /etc/acpi/sleep.sh

---

### Post by mali2297 on 2007-10-25
> **nick_h said:**
> The script you need to run is /etc/acpi/sleep.sh

You will need root privileges for that one:
```

sudo /etc/acpi/sleep.sh

```

---

### Post by stinkinrich88 on 2007-10-26
hey, thanks, but running that script does absolutely nothing. No terminal output or anything. Even when sudo.

---

### Post by mali2297 on 2007-10-26
> **stinkinrich88 said:**
> hey, thanks, but running that script does absolutely nothing. No terminal output or anything. Even when sudo.

Try
```

sudo /etc/acpi/sleep.sh force

```

(From this thread: [http://ubuntuforums.org/showthread.php?t=227676](http://ubuntuforums.org/showthread.php?t=227676) )

---

### Post by stinkinrich88 on 2007-10-27
ahhh, brilliant! thanks! anyone know if this is the same for all distros?

---

### Post by nick_h on 2007-10-27
No it will be different in other distros. Have a look in */usr/lib/hal/scripts/linux/hal-system-power-suspend-linux* to get an idea of the scripts some other OSs use.

---

### Post by stinkinrich88 on 2007-10-27
ok, fair enough, thanks!

---

