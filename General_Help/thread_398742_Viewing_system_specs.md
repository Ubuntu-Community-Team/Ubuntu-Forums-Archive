---
title: "Viewing system specs"
date: 2007-04-01
forum: General Help
---

### Post by SBFC on 2007-04-01
Hello all, how do I view my system specs? Or rather, view the specs that Xubuntu thinks I have, such as RAM and CPU speed?

I'm asking because an app of mine thinks I have a 1.0Ghz proc when in fact I have a 2.2Ghz. I wanted to check if it's my system that thinks this, or if it's just restricted to the app.

Thanks.

---

### Post by alien21010 on 2007-04-01
I think the commands you are looking for are:

cat /proc/cpuinfo
cat /proc/meminfo

Those should tell you what your computer currently sees.

---

### Post by taurus on 2007-04-01
Sounds to me like you have an AMD64 and you are using powernowd.

---

### Post by ajgreeny on 2007-04-01
To get a full list of everything on your machine type the command **sudo lshw** in a terminal.

---

### Post by SBFC on 2007-04-01
> I think the commands you are looking for are:

cat /proc/cpuinfo
cat /proc/meminfo

> To get a full list of everything on your machine type the command sudo lshw in a terminal.

Those were exactly what I was looking for, thanks to the both of you.

> Sounds to me like you have an AMD64 and you are using powernowd.

After viewing the output from those above suggested commands, my system does indeed think I have a 1.0Ghz proc. And my proc is indeed an AMD64...unfamiliar with powernowd though. Searching the forums to find out more about it.

Thanks everybody.

Edit:

Forgot to ask, does this mean my proc is actually being treated as a 1.0Ghz? I'm essentially using only half of my processing power?

---

### Post by qpieus on 2007-04-01
> **ajgreeny said:**
> To get a full list of everything on your machine type the command **sudo lshw** in a terminal.
Cool, thanks for that. I did not know this command.

---

### Post by alien21010 on 2007-04-01
It depends, if you have an AMD chip it is possible that the 1.0Ghz is your actual clock speed, since AMD's clock lower than the speed they advertise, but perform comparably to faster Intel chips...  What kind of processor do you actually have?

---

### Post by SBFC on 2007-04-01
AMD Athlon 64 Processor 3500+

---

### Post by liviubero on 2007-09-26
> **ajgreeny said:**
> To get a full list of everything on your machine type the command **sudo lshw** in a terminal.

Wow!
This command is the best tool I ever saw for getting system information.
It even saves the output as html:

sudo lshw -html>>systemInfo.html

There is also the GUI for it: lshw-gtk

---

