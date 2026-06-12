---
title: "difference between directories?"
date: 2007-07-09
forum: General Help
---

### Post by Scroopy on 2007-07-09
Hello, I'm new to this linux stuff,,, and I was just wondering if someone could clarify something for me.  When I execute the 'cd ..' command, I can end up at one of the following places:

:/$
:~$
:/home$
:/root$

My question is, what is the difference between these directories?

---

### Post by bodhi.zazen on 2007-07-09
:/$            =  root or the top. ls / to see what is in it

/ = the first slash in /home/user_name or /usr/bin or ... well you get it


:~$           = ~ is short hand for /home/username

:/home$    = /home  ls /home and you will see all the user name dirctories

:/root$      = /root = root's home (it is in /root rather then /home/root )

HTH

[http://doc.gwos.org/index.php/FileLocations](http://doc.gwos.org/index.php/FileLocations)

---

### Post by marsbt on 2007-07-09
> **Scroopy said:**
> When I execute the 'cd ..' command, 

Just for your info: The [FONT="Courier New"]cd ..[/FONT] command takes you one directory higher in the tree from the current position. You can find out which directory you are currently in by using the command [FONT="Courier New"]pwd[/FONT]  - print working directory

---

