---
title: "Problem running programs"
date: 2007-10-29
forum: General Help
---

### Post by Irti on 2007-10-29
hey..... i installed some programs using deb files but those applications dont appear in the main menu...i dont know the commands to run those programs so i cant even use alt+f2.   like i installed the widget factory using a deb file but then its not there in the menus ...and i dont know the command to run them........plzzz help

---

### Post by Partyboi2 on 2007-10-29
try 
```
gwf
```that should work.
:)

---

### Post by mali2297 on 2007-10-29
A general tip is to use the command *apropos* in the terminal, from the man page:
> 
apropos  searches  a  set  of  database  files containing short descriptions of system commands for keywords and  displays  the result on the standard output.


In your case, try
```

apropos 'widget factory'

```
Then you *might* find the name of the executable.

---

### Post by Irti on 2007-10-30
thanx ppl....gona try it out

---

