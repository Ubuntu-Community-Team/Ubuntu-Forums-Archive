---
title: "adept --&gt; synaptic"
date: 2007-01-09
forum: General Help
---

### Post by falela on 2007-01-09
Hi, are these 2 compatible?  I am sicking tired of adept crashing on me every 10-15min or so (very frustrating ](*,) ), I would like to try out synaptic, but don't know if they use the same database, so that everything is in sync.  
Thanks

---

### Post by cmost on 2007-01-09
They are both frontends to Apt.

---

### Post by taurus on 2007-01-09
Yes, they are.  Or you can run it from a terminal.

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude install **program_name**
```

---

### Post by cmost on 2007-01-09
You might want to be careful with Aptitude though.  I find that it often does it's thing without confirmation and also can disregard dependency issues, etc. if you let it.

Better is to use classic apt-get at the command line.
Example:

$sudo apt-get update
$sudo apt-get upgrade
$sudo apt-get install program_name

Your chances of screwing something up this way are lessened than with Aptitude.

---

### Post by falela on 2007-01-10
Thanks.
Is apt-get & aptitude interchangable.  apt-get install a program, then aptitude remove the same program.  Would this cause trouble?

I read in the forum that aptitude can remove all dependency when you remove an app, is it the only major different between the 2?

Also, is it just me, or is Adept don't behave nicely with you guys too?  (I am using Kubuntu Edgy amd64)

---

