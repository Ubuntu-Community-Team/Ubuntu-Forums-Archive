---
title: "Bleachbit"
date: 2013-12-11
forum: General Help
---

### Post by Silvernail on 2013-12-11
After reading on this website, I decided to go with 'bleachbit' over 'computer-janitor'.

Is the error message below normal? Is something missing on my system? Is it safe to proceed with it?

```

dave@Dafydd:~$ bleachbit  -p
info: starting BleachBit version 0.9.1
Traceback (most recent call last):
  File "/usr/bin/bleachbit", line 47, in <module>
    bleachbit.CLI.process_cmd_line()
  File "/usr/share/bleachbit/bleachbit/CLI.py", line 189, in process_cmd_line
    preview_or_clean(operations, False)
  File "/usr/share/bleachbit/bleachbit/CLI.py", line 105, in preview_or_clean
    worker = Worker.Worker(cb, really_clean, operations).run()
  File "/usr/share/bleachbit/bleachbit/Worker.py", line 67, in __init__
    raise RuntimeError("No work to do")
RuntimeError: No work to do
dave@Dafydd:~$ 

```

Manual tells me:
>        -p, --preview        preview files to be deleted and other changes

---

### Post by necromonger on 2013-12-11
what about ubuntu tweak?

---

### Post by Silvernail on 2013-12-11
> **necromonger said:**
> what about ubuntu tweak?

Their website says for Ubuntu 11.04 and before. Is that anything for 12.04 and after?

---

### Post by cybrsaylr on 2013-12-16
Bleachbit works very good to clear out the crap files that build up.
Just make use you get the two versions, Bleachbit and Bleachbit as Administrator.

[http://bleachbit.sourceforge.net/](http://bleachbit.sourceforge.net/)

---

### Post by Frogs Hair on 2013-12-16
Bleachbit run without elevated privileges/root will display permission warnings and with any cleaner make sure you understand the cleaning options you select.

---

