---
title: "need help w/ script"
date: 2005-07-08
forum: General Help
---

### Post by foobar on 2005-07-08
i am trying to write a shell script that will run this command-
```
./srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate

```
i know that this should be simple, but i cannot fig it out.

---

### Post by frodon on 2005-07-08
I supose you use bash (I use tcsh) but it should be the same. Open a new file named xxxx.bash and edit it like that: ```
#!/bin/bash -f
./srcds_run -console -game cstrike +map de_dust -maxplayers 16 -autoupdate
``` and then do a sudo chmod 775 xxxx.bash and it will be ok. To run the script just type the name of the file then enter. If you can't run the script everywhere (from any repertory) add the path of your script in $PATH  environement variable.

---

### Post by foobar on 2005-07-08
would naming it xxxx.sh be any different?

---

### Post by frodon on 2005-07-08
Choose the name you want, you can also put the extension you want (for exemple myscript.foobar !).
If you want your script to be executable everywhere do : ```
echo $PATH
```it will show you in which repertories the system look for scripts (generally /bin). Paste you script in one of these repertories and you will be able to run your script everywhere.

---

