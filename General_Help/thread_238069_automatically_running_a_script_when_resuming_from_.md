---
title: "automatically running a script when resuming from hibernate"
date: 2006-08-17
forum: General Help
---

### Post by abandoned_hussam on 2006-08-17
[SIZE=3]Is is possible to have ubuntu automatically run /usr/bin/somescript.sh on resume from hibernate?
Thanks in advance.
[/SIZE]

---

### Post by yopnono on 2006-08-17
Try put you script in /etc/acpi/resume.d and make sure it is executable and set to root

---

### Post by abandoned_hussam on 2006-08-17
ok done, now do I reboot or is a 'sudo /etc/init.d/acpid restart' enough?

---

### Post by yopnono on 2006-08-17
Normally the resume script check the resume.d folder and excecutes all script in it.  So just try to suspend / hibernate and see if the script is executed.

If not check logs and/or reboot and try again. Also you can try to run the script from terminal and see whats happening.

from the resume.sh script.
#```
!/bin/bash

# Source from /etc/acpi/resume.d/
for SCRIPT in /etc/acpi/resume.d/*.sh; do
  . $SCRIPT
done
```

---

### Post by abandoned_hussam on 2006-08-17
Ok I tried hibenating from the log out menu. When I resumed, the script I placed in resume.d was correctly executed. Thank you so much for your help. :)

---

