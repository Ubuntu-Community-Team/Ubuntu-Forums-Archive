---
title: "how to list number of processes for every user"
date: 2007-11-05
forum: General Help
---

### Post by Jubufreak on 2007-11-05
Hi everyone...i m really new to bash script...and i was wondering if there is a way to list the number of processes for everyuser...

I was told it has something to do with using /etc/passwd ... but i dont know what parameters or other commands to use...can i use grep command (?)

---

### Post by dcstar on 2007-11-05
> **Jubufreak said:**
> Hi everyone...i m really new to bash script...and i was wondering if there is a way to list the number of processes for everyuser...

I was told it has something to do with using /etc/passwd ... but i dont know what parameters or other commands to use...can i use grep command (?)

```
man ps
```

---

### Post by ardchoille42 on 2007-11-05
You can install and use htop - it's in the repos. htop is like top on steroids.. very customisable.

---

### Post by Jubufreak on 2007-11-06
#!/bin/bash
cat /etc/passwd | cut -d: -f 1
for i in $(cat /etc/passwd | cut -d: -f 1)
do
Numprocess=$(ps -u $i | wc -l) 
let Numprocess=Numprocess-1;
echo -e "Users: "$i" Number of processes for user:"$Numprocess
done

---

