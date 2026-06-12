---
title: "Problem with &quot;Ubuntu software&quot;"
date: 2017-07-01
forum: General Help
---

### Post by ordak on 2017-07-01
Hi,

Maybe due to last update, "Ubuntu software" does not show many of it's softwares. Different categories show only a small number of softwares. I am using Ubuntu 16.04.2 LTS.

---

### Post by kc1di on 2017-07-01
Hello ordak and Welcome to Ubuntu,

Go to a terminal and type the following commands one at a time and see if that helps.

```
sudo apt-get update
sudo apt-get upgrade
```

post any error messages you get here.

---

### Post by ordak on 2017-07-01
> **kc1di said:**
> Hello ordak and Welcome to Ubuntu,

Go to a terminal and type the following commands one at a time and see if that helps.

```
sudo apt-get update
sudo apt-get upgrade
```

post any error messages you get here.

After shutting down then turning on the Ubuntu PC, the problem seems to be gone. Even before executing the commands.

---

### Post by Autodave on 2017-07-01
I would still run those commands to make sure that the system is updated.  I usually do that once a week.

---

### Post by kc1di on 2017-07-01
Glad it's working but still run the commands after you do run these also:
```
sudo apt-get autoclean
sudo apt-get clean
```

Also if everything is still working please mark the thread as solved. 
Cheers!

---

