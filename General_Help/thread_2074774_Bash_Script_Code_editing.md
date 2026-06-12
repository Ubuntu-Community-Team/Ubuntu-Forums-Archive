---
title: "Bash Script Code editing"
date: 2012-10-22
forum: General Help
---

### Post by ThethundarBird on 2012-10-22
```
#!/bin/bash

gnome-terminal --tab -e " ubuntu-tweak - the symbol i want -sudo cpulimit -e ubuntu-tweak -l 50  "
```

this is for just instance for what i want to do , i want to execute in one tab terminal two commands ,so i need the symbol used to let him undesrstand that this is a second command after the first one

---

### Post by pholden on 2012-10-22
$ foo && bar # run command *foo*, if command returns successful also run command *bar*

---

### Post by ThethundarBird on 2012-10-22
> **pholden said:**
> $ foo && bar # run command *foo*, if command returns successful also run command *bar*

"&&" as symbol doesnt work , i tried it

for example try 
```
#!/bin/bash

gnome-terminal --tab -e " gedit && sudo cpulimit -e ubuntu-tweak -l 50  "
``` 

will not work

---

### Post by Vaphell on 2012-10-22
try
```
gnome-terminal --tab -e "sh -c 'gedit; sudo cpulimit -e ubuntu-tweak -l 50;'"
```

---

### Post by ThethundarBird on 2012-10-22
> **Vaphell said:**
> try
```
gnome-terminal --tab -e "sh -c 'gedit; sudo cpulimit -e ubuntu-tweak -l 50;'"
```

It works , thank u sir . i just wonder  how it works , what is the meaning of sh-c and how it works

---

### Post by Vaphell on 2012-10-23
sh is one of shells, -c tells it to execute given commands.
It's like running a script but with code explicitly given inline in a parameter string, instead of a file.

instead of
**script.sh:** [I]gedit; sudo cpulimit -e ubuntu-tweak -l 50;
sh script.sh (or ./script.sh)[/I]
you go with
*sh -c 'gedit; sudo cpulimit -e ubuntu-tweak -l 50;'*

apparently **gnome-terminal** likes to get a single command to execute and wrapping the sequence of commands in **sh -c** makes them act that way - **gnome-terminal** deals only with **sh**

---

