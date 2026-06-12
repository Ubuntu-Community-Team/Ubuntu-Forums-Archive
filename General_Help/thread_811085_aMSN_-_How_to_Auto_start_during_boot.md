---
title: "aMSN - How to Auto start during boot?"
date: 2008-05-28
forum: General Help
---

### Post by Xirowei on 2008-05-28
Is there a way to make aMSN start up automatically when Ubuntu starts up?

I only know the procedure to auto start pidgin which was:

System-Preferences-Sessions
Start-up programs
New
Name : Pidgin
Command: ***pidgin***
Then go to Sessions Options and save it.

However, for aMSN, what is the Command i should use?

---

### Post by zeronothing on 2008-05-28
if you go to "system -> preferences -> sessions" you should have a window up for sessions preferences. click the add button, enter in the name, the command to open "aMSN" ( it is usually located in the /usr/bin directory). add a comment and your done. hopefully when you restart your computer it will load during startup.

---

### Post by zeronothing on 2008-05-28
one way to find out what the command is, open up synaptic and search for amsn. after your search results, highlight "amsn" and click properties. then go under the tab installed files. in their you should be able to find out where everything is installed at. just find the executable for amsn from there.

---

### Post by Xirowei on 2008-05-29
> **zeronothing said:**
> if you go to "system -> preferences -> sessions" you should have a window up for sessions preferences. click the add button, enter in the name, the command to open "**aMSN**" ( it is usually located in the /usr/bin directory). add a comment and your done. hopefully when you restart your computer it will load during startup.


Thanks for your advice, but i found out the command is **amsn**, Not **aMSN**. It is case sensitive in Linux.

---

