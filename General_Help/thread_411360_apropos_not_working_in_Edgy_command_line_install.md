---
title: "apropos not working in Edgy command line install"
date: 2007-04-16
forum: General Help
---

### Post by Durito on 2007-04-16
Does anyone know why 'apropos' wouldn't be working in my Edgy command line install? It returns 'command: nothing appropriate' everytime. What's going on? It works fine with a server install, oddly enough. Tried 'mandb -create', in case the database was corrupted, but it found no changes. Grrr. Running Edgy on a TP600e. Pardon the formatting--posting this from links.

---

### Post by azzid on 2007-06-09
Did you find a sollution to this?

Just installed Ubuntu 6.06.1 to build myself a new firewall.

apropos never finds anything, man however works perfectly.


***edit: *sudo mandb --create* did the job! =)

---

### Post by dcstar on 2007-06-09
```
man -k keyword
```

---

### Post by azzid on 2007-06-09
```
man -k *keyword*
```
worked just as bad as 
```
apropos *keyword*
```
until
```
sudo mandb --create
```
was executed

---

