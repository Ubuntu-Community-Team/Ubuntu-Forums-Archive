---
title: "Help to write a script"
date: 2007-04-16
forum: General Help
---

### Post by bofphile on 2007-04-16
I would like to write a script that execute this command after my laptop has resumed from sleep:
hdparm -B 255 /dev/hda

I know I have to put it in /etc/acpi/resume.d/ but I don't know how to write it (except for the beginning #! /bin/bash :)) .

Thanks.

---

### Post by energiya on 2007-04-16
If you want to build a script that executes that command, just..
```

#!/bin/bash
hdparm -B 255 /dev/hda

```
Hope I didn't missunderstood what you are trying to say.

---

### Post by bofphile on 2007-04-16
I didn't think this was that simple !
Thanks a lot. :D

---

