---
title: "Konsole 'bash:  command not found'"
date: 2007-03-22
forum: General Help
---

### Post by mborrill on 2007-03-22
Any idea why Im getting bash: command not found and most commands in konsole ?

Thanks In Advance ;-)

---

### Post by taurus on 2007-03-22
Can you give an example of some of the commands you want to run from a terminal?

---

### Post by mborrill on 2007-03-22
> **taurus said:**
> Can you give an example of some of the commands you want to run from a terminal?

ok sorry its just happening when I try and run a python script , I type particleinvaders.py in konsole and get command not found , this worked yesterday lol

---

### Post by taurus on 2007-03-22
Maybe because **particleinvaders.py** is not in your path or you are not in the right directory when you try to run it.

---

### Post by JRanch on 2007-08-14
Affix "./" to the beginning of the command to force bash to check the working directory. 

e.g. "./particleinvaders.py"

Or you can permanently add the current working directory to the path variable by typing "PATH=.:$PATH"

-jr

---

