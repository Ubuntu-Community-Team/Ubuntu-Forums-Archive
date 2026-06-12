---
title: "Hitting tab in terminal to complete commands"
date: 2007-01-04
forum: General Help
---

### Post by strabes on 2007-01-04
Hitting tab to complete commands in gnome-terminal no longer works. Does anyone know how to fix this?

[EDIT]

I found out how to fix this in #linux.

sudo nano /etc/bash.bashrc 
Uncomment the 3 lines about enabling bash completion in interactive shells

It's as easy as that!!!

---

### Post by koenn on 2007-01-04
it's called command completion and is a feature of the shell.

I've read that in Edgy the default shell is dash, no longer bash, 
so maybe you have to set some dash preference to make it work ? 

to test : 
type /bin/bash  in a terminal and see if the behaviour changes.

---

### Post by harun on 2007-04-12
Anyone know why the default is to have command completion off?

---

