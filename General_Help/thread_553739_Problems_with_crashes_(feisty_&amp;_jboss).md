---
title: "Problems with crashes (feisty &amp; jboss)"
date: 2007-09-18
forum: General Help
---

### Post by johaerik on 2007-09-18
Hi,

I'm quite a noob when it comes to the really low level ins & outs of linux. I've got a Feisty server 7.04 set up with only a jboss server installed on it.
Now the main problem I have is that quite often the ubuntu server will crash, just hang, there is no console so I cant see any error messages.... is there anywhere I can look to get to the bottom of this?

I had the same problem when I ran VMWare server on the machine, only it would happen more often.

Any suggestions?

Cheers
Johan

---

### Post by Robsteranium on 2007-12-04
Have you tried looking in the logs?
e.g.
For ubuntu: */var/log/messages* and 
for JBoss: *$JBOSS_HOME/server/default/log*

I've been running into problems with JBoss eating up all the memory!  Make sure you're not giving the java process more than you have to spare.  There are some good tips [[COLOR="RoyalBlue"]here[/COLOR]]("http://rimuhosting.com/howto/memory.jsp").

---

