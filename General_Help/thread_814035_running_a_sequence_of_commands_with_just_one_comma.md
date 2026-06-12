---
title: "running a sequence of commands with just one command"
date: 2008-05-31
forum: General Help
---

### Post by amit1702 on 2008-05-31
hi everybody...
i want to execute a sequence of commands with just one command for this...
i saved all the commands in one text file named dict
and i am executing 
./dict in the correct directory...
it gives

amit@param:~$ ./dict
bash: ./dict: Permission denied

what's wrong with it..
please help...

---

### Post by x1a4 on 2008-05-31
Hi,

Make sure you specified the shell you want to use to process your commands on the first line of the script, ie: ```
#!/bin/bash
```  Also, make sure you set the execute bit on the file ```
chmod +x ./dict
```

Or, prepend ./dict with **sh**
```
sh ./dict
```

---

### Post by amit1702 on 2008-05-31
thanx a lot...
it was the mode creating the problem...
can we produce a delay(of say 2 seconds) between two perticuler consecutive commands in such a situation...
thanx...

---

### Post by x1a4 on 2008-05-31
> **amit1702 said:**
> thanx a lot...
You're welcome.

> can we produce a delay(of say 2 seconds) between two perticuler consecutive commands
```

#!/bin/bash
command_1
sleep 2
command_2

```

---

### Post by dashnak on 2008-05-31
Yes, you can, check
```
man sleep
```

---

### Post by dashnak on 2008-05-31
> **x1a4 said:**
> You're welcome.


```

#!/bin/bash
command_1
sleep 2
command_2

```

You would have to do "sleep2 && command_2"

---

