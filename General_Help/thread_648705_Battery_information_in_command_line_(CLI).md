---
title: "Battery information in command line (CLI) ?"
date: 2007-12-23
forum: General Help
---

### Post by altonbr on 2007-12-23
How do I find my laptop's battery information while running in the CLI?

I've ran:
```
$ acpi
$ apm
$ battstat
```

But none of them are able to find any information.

---

### Post by Craigus on 2007-12-23
Something like

>  cat /proc/acpi/battery/BAT0/whatever file you want to list

Note that your battery may be BAT1, just browse in /proc/acpi/battery

---

### Post by jualin on 2008-06-23
It is probably kind of late for this and maybe you found out the solution already but for anyone wanting to see the battery status on the Command Line the command is > asci -v.

---

