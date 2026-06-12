---
title: "Curious..."
date: 2008-07-06
forum: General Help
---

### Post by davidpeace on 2008-07-06
What does "sudo" mean? And why that to be in root/admin mode?:?::?:

---

### Post by Tomatz on 2008-07-06
> **davidpeace said:**
> What does "sudo" mean? And why that to be in root/admin mode?:?::?:

Super user do ;)

---

### Post by DGortze380 on 2008-07-06
> **Tomatz said:**
> Super user do ;)

thats actually a misconception .. sudo is a UNIX command, you will find it on almost all UNIX systems back to BSD. su originally stood for SWITCH user, not super user. If you switch user and don't specify a username the default is to switch to root.

Sudo allows you to run commands as root without logging in to the root account. It is useful in giving users root access to only certain commands. This maintains a higher level of system security.

Everything above is definitely true. As to were the actual command name came from, my best guess, and logical answer would be a combination of the su command and the do command...
the logic would be something like: switch user to root and do some command.

---

### Post by Tomatz on 2008-07-06
> **DGortze380 said:**
> thats actually a misconception .. sudo is a UNIX command, you will find it on almost all UNIX systems back to BSD. su originally stood for SWITCH user, not super user. If you switch user and don't specify a username the default is to switch to root.

Sudo allows you to run commands as root without logging in to the root account. It is useful in giving users root access to only certain commands. This maintains a higher level of system security.

Everything above is definitely true. As to were the actual command name came from, my best guess, and logical answer would be a combination of the su command and the do command...
the logic would be something like: switch user to root and do some command.

Yes it once meant switch user but [B]wasn't UNIX once called UNICS?
[/B]
sudo stands for **super user do** as su now stands for **super user.**

*tomatz dons flame retardant suit*

---

### Post by DGortze380 on 2008-07-06
> **Tomatz said:**
> Yes it once meant switch user but [B]wasn't UNIX once called UNICS?
[/B]
sudo stands for **super user do** as su now stands for **super user.**

*tomatz dons flame retardant suit*

I'm not going to flame you... but I disagree. 

There is no 'super user' ... there is root. thus su is switch user not super user.  

Even if we say super user is a more common term today, we're talking about where the command sudo came from. sudo has existed from day 1 so it would have come from 'SWITCH user then do'. not super user.

As far as UNIX and UNICS, I don't know.

---

### Post by Tomatz on 2008-07-06
> **DGortze380 said:**
> I'm not going to flame you... but I disagree. 

There is no 'super user' ... there is root. thus su is switch user not super user.  

Even if we say super user is a more common term today, we're talking about where the command sudo came from. sudo has existed from day 1 so it would have come from 'SWITCH user then do'. not super user.

As far as UNIX and UNICS, I don't know.

A history of unix

[http://www.levenez.com/unix/history.html](http://www.levenez.com/unix/history.html)

Super user

[http://en.wikipedia.org/wiki/Root_user](http://en.wikipedia.org/wiki/Root_user)

---

### Post by DGortze380 on 2008-07-06
> **Tomatz said:**
> A history of unix

[http://www.levenez.com/unix/history.html](http://www.levenez.com/unix/history.html)




ok

> **Tomatz said:**
> 
Super user

[http://en.wikipedia.org/wiki/Root_user](http://en.wikipedia.org/wiki/Root_user)

first, I don't count wikipedia as a reliable source.
second, even if I were to concede that super user is a more common term today (more common, though not correct), we're talking about the origins of the sudo command, which come from the original UNIX command su, which at that time meant SWITCH user (i would argue that it still does, but that a whole other argument).

---

### Post by rraj.be on 2008-07-06
> **davidpeace said:**
> What does "sudo" mean? And why that to be in root/admin mode?:?::?:

I think these links will help you

[http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html]("http://www.developertutorials.com/tutorials/linux/using-sudo-050511/page1.html")

[http://www.megacoder.com/files/sudo-tutorial-en_US/]("http://www.megacoder.com/files/sudo-tutorial-en_US/")

[http://www.psychocats.net/ubuntu/graphicalsudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

---

### Post by Tomatz on 2008-07-06
> **DGortze380 said:**
> ok



first, I don't count wikipedia as a reliable source.
second, even if I were to concede that super user is a more common term today (more common, though not correct), we're talking about the origins of the sudo command, which come from the original UNIX command su, which at that time meant SWITCH user (i would argue that it still does, but that a whole other argument).

What a colourful discussion. Oops sorry i mean colorful ;)

Catch my drift?

---

### Post by txcrackers on 2008-07-06
> **tomatz said:**
> what A Colourful Discussion. Oops Sorry I Mean Colorful ;)

Catch My Drift?
+1

---

### Post by bodhi.zazen on 2008-07-06
> **Tomatz said:**
> What a colourful discussion. Oops sorry i mean colorful ;)

Catch my drift?

:lolflag:

Actually, you are both right and both wrong.

sudo means (from the sudo home page) :
> Sudo (su "do")[http://www.sudo.ws/sudo/sudo.html](http://www.sudo.ws/sudo/sudo.html)

But su is ambiguous :)

from the UNIX man pages :

> su - change user ID or become super-user[http://unixhelp.ed.ac.uk/CGI/man-cgi?su](http://unixhelp.ed.ac.uk/CGI/man-cgi?su)

su is also refers to as switch user and, from the BSD man pages :

> **su**  - substitute user identity[http://www.gsp.com/cgi-bin/man.cgi?section=1&topic=su](http://www.gsp.com/cgi-bin/man.cgi?section=1&topic=su)

Although the "modern" definition is* super user do*

The "official" definition of sudo is :

**substitute user do**

:lolflag:

---

### Post by Tomatz on 2008-07-06
> **bodhi.zazen said:**
> :lolflag:

Actually, you are both right and both wrong.

sudo means (from the sudo home page) :
[http://www.sudo.ws/sudo/sudo.html](http://www.sudo.ws/sudo/sudo.html)

But su is ambiguous :)

from the UNIX man pages :

[http://unixhelp.ed.ac.uk/CGI/man-cgi?su](http://unixhelp.ed.ac.uk/CGI/man-cgi?su)

su is also refers to as switch user and, from the BSD man pages :

[http://www.gsp.com/cgi-bin/man.cgi?section=1&topic=su](http://www.gsp.com/cgi-bin/man.cgi?section=1&topic=su)

Although the "modern" definition is* super user do*

The "official" definition of sudo is :

**substitute user do**

:lolflag:

Thanks for the info :)

---

### Post by davidpeace on 2008-07-07
To all:

Thanks. (didn't know what I started:redface:

---

