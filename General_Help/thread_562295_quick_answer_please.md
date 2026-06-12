---
title: "quick answer please"
date: 2007-09-28
forum: General Help
---

### Post by caprisone on 2007-09-28
how can i change permissions of file  sources.list ????
i tried to do chmod +rwx source.list    and this operation is not allowed  :/

---

### Post by cmnorton on 2007-09-28
If you want to edit it, sudo vi /etc/apt/sources.list, and substitute your favorite editor for vi.

If you want to change the permissions preface your command with sudo.

---

### Post by pointone on 2007-09-28
You want it to be executable? :|

---

### Post by caprisone on 2007-09-28
no. i've instaled ubuntu recently and i'm starting to explore it. in this case i want to change the appearence of it, and i have to add a line to this file. and it's permissions didnt allow me to do it

---

### Post by caprisone on 2007-09-28
i've preceded my comand with sudo and i couldn't change the permissions yet!!!! 
i typed:   sudo chmod +x sources.list
is this correct??

---

### Post by Caffeine_Junky on 2007-09-28
hello there :)

I am not sure what you are trying to do (by attempting to make that file executable) ..but if you just want permission to EDIT and SAVE text changes in that file well you use the following command:

sudo gedit /etc/apt/sources.list

heh learning is so much fun heh? :)

I assume you are using ubuntu ?

---

### Post by wirelessmonkey on 2007-09-28
Unless you know EXACTLY what you're doing, it is ALWAYS a bad idea to go changing permissions on any file or directory that is not under /home  DON'T DO IT.

---

