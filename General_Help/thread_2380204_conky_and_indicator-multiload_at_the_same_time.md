---
title: "conky and indicator-multiload at the same time"
date: 2017-12-14
forum: General Help
---

### Post by rosika on 2017-12-14
Hi altogether,


I´ve got **indicator-multiload** running on my system all the time. It shows the usage of the processor, RAM, netowrk and HDD.
Now I am experimenting with different **conky**-configs. 


As conky is a *system-monitor* as well I have two system-monitors running at the same time which at least in part are monitoring the same processes (RAM, up-and download, cpu ...).
It all works very well.  Indicator-multiload and conky do their respective jobs flawlessly. 


Just out of curiosity: My question is: Are there any objections as far as *running two system-monitors at the same time* is concerned?


At least I know the following: It´s perfectly legitimate to run more than one instance of conky at the same time:


> "However, you can have two or more instances of Conky running at the same time with different config files, e.g.


conky -c ~/.config/conky/conky1.conf
conky -c ~/.config/conky/conky2.conf
You might consider launching it in its own window (-o arg) in this case." 
( [https://github.com/brndnmtthws/conky/wiki/FAQ](https://github.com/brndnmtthws/conky/wiki/FAQ) )


Thanks in advance.
Greetings.
Rosika  


P.S.: 
System: Linux/Lubuntu 16.04.3 LTS, 64bit

---

### Post by Habitual on 2017-12-14
been there, done that!

> 1 monitor is fine, IMHO.

---

### Post by vasa1 on 2017-12-14
> **rosika said:**
> ...
Just out of curiosity: My question is: Are there any objections as far as *running two system-monitors at the same time* is concerned?
...
Having two system monitors showing the same data is redundant. Is there any pressing reason to do so?

---

### Post by rosika on 2017-12-14
@ Habitual:
thanks for your opinion.

@ vasa1:

Hi.

> [COLOR=#000000]Is there any pressing reason to do so?[/COLOR]
No special reason in particular. 
[COLOR=#000000][FONT=Verdana]I just asked because I want to run conky from time to time. And indicator-multiload keeps running per default. I really don´t want to kill one system-monitor each time just to be able to run another one.




[/FONT][/COLOR]

---

### Post by deadflowr on 2017-12-14
> Are there any objections as far as running two system-monitors at the same time is concerned?
No
People run multiple monitors all the time, if only to compare and contrast outputs.
(Like running gnome system-monitor and top, and maybe also htop or even conky at once)

---

### Post by rosika on 2017-12-16
Hi deadflowr,

thanks for your answer. I´m very pleased to learn that all the scenarios you mentioned work well.
Comparing and contrasting outputs is my main objective as well (at least from time to time).

Have a nice weekend.
Greetings.

Rosika

---

