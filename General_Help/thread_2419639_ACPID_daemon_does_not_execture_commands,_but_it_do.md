---
title: "ACPID daemon does not execture commands, but it does when launched from terminal"
date: 2019-05-24
forum: General Help
---

### Post by mijji2 on 2019-05-24
I am litterally going mad on this issue. I just want to execute a simple script when the headphone jack is plugged in, but the acpid daemon just does not execute the script as it should. However if i open a terminal and type ```
sudo acpid
``` that will work?!
Here is the output of the daemon

```

[FONT=monospace][COLOR=#000000]mag 24 12:20:25 lorenzo-Inspiron-15-5578 acpid[5904]: executing action "/etc/acpi/unplug.sh"[/COLOR]
mag 24 12:20:25 lorenzo-Inspiron-15-5578 acpid[5848]: action exited with status 0
mag 24 12:20:25 lorenzo-Inspiron-15-5578 acpid[5848]: 1 total rule matched
mag 24 12:20:25 lorenzo-Inspiron-15-5578 acpid[5848]: completed input layer event "jack/headphone HEADPHONE unplug"
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5848]: received input layer event "jack/headphone HEADPHONE plug"
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5848]: rule from /etc/acpi/events/headphones-plug matched
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5916]: executing action "/etc/acpi/plug.sh"
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5848]: action exited with status 0
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5848]: 1 total rule matched
mag 24 12:20:26 lorenzo-Inspiron-15-5578 acpid[5848]: completed input layer event "jack/headphone HEADPHONE plug"
[/FONT]
```

So it looks like it is working, but the commands are not executed.

---

### Post by coffeecat on 2019-05-24
Support, not chat.

*Thread moved to **General Help**.*

---

