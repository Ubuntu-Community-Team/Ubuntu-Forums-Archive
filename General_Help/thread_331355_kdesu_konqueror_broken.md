---
title: "kdesu konqueror broken"
date: 2007-01-04
forum: General Help
---

### Post by Zill on 2007-01-04
Dapper kdesu konqueror used to open root konqueror as expected.
Now it fails to open konqueror although other kdesu commands still work OK as does user konqueror.  kdesu still requests password but then shows the following error in konsole:

~$ kdesu konqueror
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ScimInputContextPlugin()

Any ideas please?

---

### Post by Zill on 2007-01-05
The answer appears to be one or both of the following commands:
> 
dcopserver_shutdown
kdeinit

I tried this first as a user and then with sudo so am not sure exactly which command or user/sudo actually cleared the problem.  However, it's gone now and kdesu konqueror again works as expected :-)
Just be warned that these commands immediately log you out of kde and then go back to the kdm screen so save all work first ;-)

---

