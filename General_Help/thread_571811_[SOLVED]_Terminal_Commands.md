---
title: "[SOLVED] Terminal Commands"
date: 2007-10-09
forum: General Help
---

### Post by kshane on 2007-10-09
Is it possible to give multiple commands (at least 2) on a command line?  If so, what is used to separate the commands?

Thanks!

Kevin

---

### Post by bodhi.zazen on 2007-10-09
command 1; command 2
[indent]Runs 1 then 2[/indent]

command 1 && command 2
[indent]runs 1, 2 only if 1 completes without error[/indent]

command 1 || command 2
[indent]runs 2 only if 1 fails[/indent]

command 1 \
command 2
[indent]use \ to continue commands on multiple lines[/indent]

---

### Post by kshane on 2007-10-09
> **bodhi.zazen said:**
> command 1; command 2
[indent]Runs 1 then 2[/indent]

command 1 && command 2
[indent]runs 1, 2 only if 1 completes without error[/indent]

command 1 || command 2
[indent]runs 2 only if 1 fails[/indent]

command 1 \
command 2
[indent]use \ to continue commands on multiple lines[/indent]

Thank you ***very much*** for your speedy reply!  I'll make note of this so I don't have to ask again..  :)

Kevin

---

### Post by Jose Catre-Vandis on 2007-10-09
In what circumstances and exactly how would you use the fourth example?

command 1 \
command 2

It just get's upset if i try it

and any way to run command 1 and command 2 at the SAME time rather than either/or or one after the other?

---

### Post by bodhi.zazen on 2007-10-09
Sorry for the confusion 

\ = continue on a new line

you need 

command 1 ;\
command 2

You can break it up :

com\
and 1\
;\
command 2

any how you want, the point is to take :

command 1; command 2; command 3

and make it easier to read 

command 1;\
command 2;\
command 3

(Hit the <enter> key after the \ and after the last command to execute all 3)

As far as running several commands at the same time, depends on the command, try starting them in a sub shell if needed:

```
command 1 &; command 2
```

Subshell = (command 1)

```
(command 1&); command 2
```

---

### Post by Jose Catre-Vandis on 2007-10-10
Thanks [COLOR="Red"]bodhi.zazen[/COLOR], much clearer now :)

---

### Post by thirddeep on 2007-10-10
IMHO, there is no better guide than [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) for BASH scripting.

Thd.

---

### Post by kshane on 2007-10-12
> **thirddeep said:**
> IMHO, there is no better guide than [http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/) for BASH scripting.

Thd.

And thanks to you too!

Kevin

---

