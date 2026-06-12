---
title: "Can't get ubuntu in a higher resolution"
date: 2007-04-06
forum: General Help
---

### Post by rob1101 on 2007-04-06
hello all i have been using linux for a total of 2 days so i am very, very new. and please forgive me if i ask stupid questions. 

so let me give you a run down i installed ubuntu 2 days ago liked it wanted to try out some new desktop enviroments, and then wanted to get rid of some that i downloaded. but i messed it up bad, apparently i removed some things that i should not have, but that's not the point the point is that i had ubuntu up and running in 1024x768 ( in the default gnome desktop before i even downloaded anything.

due to the problems, i did a fresh install of ubuntu. i chose the option to erase the existing partitions. so now i am in a new fresh install of ubuntu but for some reason i don't have the option to put it in a resolution higher than 800x600, and for me that's not going to cut it. 

the card is an ATI Radeon X800XT

i searched through the Synaptic Package Manager and found a driver that said it supported my card. I did the only thing a n00b knows to do, which is check the box, click apply and hope it works. and of course it didn't, i don't think it did at least, well it didn't do what i wanted it to. 

so if any of you know how to fix this please reply and if you need any specs and what not just post here. 

P.S. I would like to get the card working and supported, instead of just some how making the res smaller and putting the strain on the os. 

-Thx in advance

---

### Post by burritomaster on 2007-04-06
Use envy. [Click]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by kerry_s on 2007-04-06
run> sudo dpkg-reconfigure -phigh xserver-xorg
in terminal(it's under accessories).

---

### Post by rob1101 on 2007-04-06
> **burritomaster said:**
> Use envy. [Click]("http://www.albertomilone.com/nvidia_scripts1.html")

Error: Dependency is not
satisfiable: module-assistant

---

### Post by rob1101 on 2007-04-06
> **kerry_s said:**
> run> sudo dpkg-reconfigure -phigh xserver-xorg
in terminal(it's under accessories).

*hugs*  thank you that got it working :)

---

### Post by oomingmak on 2007-04-06
> **rob1101 said:**
> Error: Dependency is not
satisfiable: module-assistant

I get exactly the same error when I try to use Envy.

Needless to say, not a word on the web site about how to resolve this issue (as if this whole graphic card fiasco is not complicated enough as it is).

:roll:

---

### Post by Antman on 2007-04-07
> **oomingmak said:**
> I get exactly the same error when I try to use Envy.

Needless to say, not a word on the web site about how to resolve this issue (as if this whole graphic card fiasco is not complicated enough as it is).

:roll:

You didn't complete a needed step.  Make sure you have all the repositories enabled (also universe and multiverse) in Synaptic.  
:guitar: 

Ant

---

### Post by carusoswi on 2007-04-08
> **burritomaster said:**
> Use envy. [Click]("http://www.albertomilone.com/nvidia_scripts1.html")

Just wanted to report that I had been searching for a solution to this problem for a couple of weeks, now.  Just came across this thread, followed the link, and the Envy worked perfectly to correct my problem.

I am new to Ubuntu and to Linux, but am amazed how many people devote what must be hours of time to make this whole thing go - amazing, refreshingly so.

Caruso

---

