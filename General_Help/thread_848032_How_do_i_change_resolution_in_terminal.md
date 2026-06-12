---
title: "How do i change resolution in terminal?"
date: 2008-07-03
forum: General Help
---

### Post by BlackSwordD2 on 2008-07-03
i want to set a launcher for a wine app to change the resolution of my desktop before starting how would i do that?

also how do i run 2 commands for a launcher?

---

### Post by NT4usB on 2008-07-04
> **BlackSwordD2 said:**
> ...also how do i run 2 commands for a launcher?
In a terminal, we would use '&&' between the commands...```
$sudo updatedb && locate somefile
```

Wonder if that would work in a launcher?

---

### Post by BlackSwordD2 on 2008-07-04
thanks mate i thought  that was the command but i dont think it works in launcher... sad day

---

### Post by drs305 on 2008-07-04
> **BlackSwordD2 said:**
> thanks mate i thought  that was the command but i dont think it works in launcher... sad day

You can just make a launcher referring to a script, with the full pathname.
In the script, just place the two commands on separate lines and they will both run. If you need time for the first to run a bit before the second starts, the simpleton's method is just stick a "sleep X" (with X being seconds) between the two. 

```

#!/bin/bash
nautilus
sleep 5 # not required
gimp

```

With the 'updatedb' command you would probably want to put in a simple sleep command or make a more complex script to wait for it to finish since it can take some time and the locate command might start running before the database was updated. Note: using updatedb with sudo gets into a whole extra discussion on how to do it.

---

