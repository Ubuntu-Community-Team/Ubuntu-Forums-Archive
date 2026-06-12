---
title: "need desktop launcher to change directory"
date: 2007-01-19
forum: General Help
---

### Post by nephish on 2007-01-19
hey there all.
i have a python app called admin.py
i want to create a desktop shortcut for it, but i need to run it from the 
/home/me/working/admin.py directory. 

i would also like to run it from the gnome-terminal

i have tried this 
gnome-terminal -execute cd /home/me/working && python admin.py

but it does not work.

any ideas ?

---

### Post by mssever on 2007-01-19
Make the following shell script, make sure it's executable, and point the launcher at that.
```
#!/bin/bash
cd /home/me/working && python admin.py
```
The deal is, cd is a shell builtin and the launcher doesn't fire up a shell.

---

### Post by nephish on 2007-01-19
cool, can i modify this so that it runs from a terminal ( i need to see error output if it dies )

thanks

---

### Post by mssever on 2007-01-19
You could point the launcher to ```
gnome-terminal --execute='/path/to/shellscript'
```

You'll also need to add the following to the end of the shellscript to keep the terminal from closing the instant your program dies: ```
[COLOR=Green]status="$?"[/COLOR]
echo -en "\n\nPress any key to exit... "
read -n 1
[COLOR=Green]exit "$status"[/COLOR]
``` Or, you could get more elaborate and include the green lines as well, though they aren't strictly necessary.

---

### Post by nephish on 2007-01-19
working great now, 
thanks !

---

