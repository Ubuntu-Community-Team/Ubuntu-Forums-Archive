---
title: "CVS repositories in Eclipse on Linux"
date: 2008-02-14
forum: General Help
---

### Post by gamelord12 on 2008-02-14
So I'm trying to link up to my school's server which contains the files I'm updating for my homework.  It would be nice to get this working on my laptop, but I get the following error when I try to navigate to the CVS pane:

Problems opening perspective 'org.eclipse.team.cvs.ui.cvsPerspective'

How do I fix this?

---

### Post by gamelord12 on 2008-02-18
Does anyone know?  If I can't get this working, I won't have any choice but to be at my desktop when I do my assignments, which means that I may not be able to go home on the weekends with just my laptop.

---

### Post by gamelord12 on 2008-02-19
Anyone?

---

### Post by #Reistlehr- on 2008-02-19
i dont use cvs, only svn, but i could suggest using the cli version of the cvs commands. 

read [http://www.faqs.org/docs/Linux-HOWTO/CVS-RCS-HOWTO.html#s4](http://www.faqs.org/docs/Linux-HOWTO/CVS-RCS-HOWTO.html#s4) for more info

That way, youd have the files, you can move them wherever, move them back, or even just make a bash script to do everyhting for you.

---

### Post by daylond on 2008-03-31
Sorry if this answer comes too late, but I had the same problem.  Turns out the way to solve it is to remove the gcj version of java, and make sure that the sun java is installed.  I fixed that myself, and it works fine now.

---

