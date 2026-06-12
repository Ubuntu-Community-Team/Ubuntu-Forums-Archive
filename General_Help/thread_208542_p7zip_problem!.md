---
title: "p7zip problem!"
date: 2006-07-03
forum: General Help
---

### Post by Gonzakpo on 2006-07-03
Hello everyone.

The title of this post it's not really exactly what i want to ask. 
It's a general problem I've been having.

I happened to me with the bittorrent oficial and now with the p7zip (7zip). 
The problem probably is very simple to solve, but I'm almost new at linux so I really don't know what to do. I search for a solution, but nothing.

The quiestin is the following: What can I do if I installed a package with synaptic and it doesn't appear in the programs menu?? also i tried to open it from a terminal, but i can't found the right command to execute it!?
Is there a command that lists all the posible commands? How do I know which is the command to open 7zip, or the bittorrent, etc? 

That's my question, hope you know the answer! 
Ok that's all. THanks!

---

### Post by Gonzakpo on 2006-07-03
I apologize because I've already found the 7zip solution
It was 7z the command

But anyway, is there a way to list all the commands? (like the ls command but for listing terminal commands)

---

### Post by bugzor on 2006-07-03
```
7z
``` runs 7zip in terminal
but file-roller should be capable to open,edit and create 7zip files after you install p7zip

you can try 'locate 7zip' 
or 'whereis 7zip'

dir /usr/bin/ 
prints every file in /usr/bin/ where all executables go (atleast should)

dir /usr/local/bin/
does same but for folder /usr/local/bin 
some executables goes there

---

### Post by Gonzakpo on 2006-07-03
Ok ..thank You Very Much For The Help!

---

### Post by Gonzakpo on 2006-07-04
another question

does anyone know to launch the bittorrent-gui? 

I've installed it from synaptic, but i don't know how to launch it. Of course it isn't on the main menu

EDIT: Erase the post please, problem solved! It was an stupid question!

---

