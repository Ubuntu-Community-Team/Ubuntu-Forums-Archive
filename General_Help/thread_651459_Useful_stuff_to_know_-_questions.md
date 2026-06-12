---
title: "Useful stuff to know - questions"
date: 2007-12-27
forum: General Help
---

### Post by Ertai87 on 2007-12-27
OK, so I have a few questions about some useful stuff I should know.  Maybe someone can help me:

1) Startup programs.  I have a bunch of processes that start on startup and are not listed in my startup manager.  I want these processes to stop starting up.  Where is a more-advanced version of my startup processes located so I can stop these from loading?  For the record, they're related to Evolution.

2) I recently began having a problem with SCIM, where the parent process starts up as a zombie.  I don't know how or why this happened, but I appear to be unable to fix it.  The program itself seems to work fine, but I'm worried that this might be part of a bigger problem.  It's also somewhat related to the previous question, as SCIM is not listed in my startup items, while it should be.

3) How can I find out when Ubuntu updates have been released and what the latest date/version for OS-related stuff is?  I haven't gotten any O updates for about half a week, and I'm wondering if something's wrong...

Thanks.

---

### Post by jken146 on 2007-12-27
> **Ertai87 said:**
> 1) Startup programs.  I have a bunch of processes that start on startup and are not listed in my startup manager.  I want these processes to stop starting up.  Where is a more-advanced version of my startup processes located so I can stop these from loading?  For the record, they're related to Evolution.
Often it is easiest to just stop the processes you don't want (System Manager) then save your session (Sessions).

> 2) I recently began having a problem with SCIM, where the parent process starts up as a zombie.  I don't know how or why this happened, but I appear to be unable to fix it.  The program itself seems to work fine, but I'm worried that this might be part of a bigger problem.  It's also somewhat related to the previous question, as SCIM is not listed in my startup items, while it should be.
You already have a thread about this.  Duplicate threads are baaaad.  Leave it alone if it isn't causing any harm (the impression I get from the other thread).

> 3) How can I find out when Ubuntu updates have been released and what the latest date/version for OS-related stuff is?  I haven't gotten any O updates for about half a week, and I'm wondering if something's wrong...
Update Manager or ```
sudo aptitude update
sudo aptitude upgrade
```
Half a week isn't a long time.  Sometimes it is much longer between updates to the repos.  Don't worry.

---

### Post by Ertai87 on 2007-12-27
For questions 1 and 2, I've been recently having a lot of computer problems (which is why I switched to Ubuntu in the first place).  I'm still going through the "I'm uber-paranoid about using the internet cause I've already been screwed once" phase, so to me anything out of the ordinary looks like a potential security risk/hacker attack.  That's why I asked those questions.

For question 3, how do I find out if I have the latest version?  Again, the "I think I'm being hacked" syndrome: How do I know that something's not blocking me from doing updates?  If I was a hacker, one of the first things I'd do would be to block the computer user from getting security updates which would alert him to my presence...

---

### Post by cdenley on 2007-12-27
To find out if you have the latest updates, you can

-System>Administration>Update Manager. It will either say "Your system is up-to-date" at the top, or list possible updates.

-System>Administration>Synaptic Package Manager, click "Reload" at the top left, select "Custom filters" at the bottom right, select Upgradable. Any packages which can be upgraded will be listed.

-Applications>Accessories>Terminal, enter the following commands
```

sudo apt-get update
sudo apt-get upgrade

```
Anything that can be updated will be.

If you want to check Ubuntu's security notices:
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

