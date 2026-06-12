---
title: "buy Ubuntu support?"
date: 2013-12-15
forum: General Help
---

### Post by msekkappan on 2013-12-15
Two of our developers are using ubuntu, and we would like to buy the support package for them because they are new to Ubuntu.  When our procurement called, they were told that we can't purchase support for 2 instances.  It has to be 5 or more.  Also, we were told to obtain free help by posting to the forums.  We are not getting satisfactory answers when we post to the forums.

Any ideas???

---

### Post by buzzingrobot on 2013-12-15
Forum posts are created and answered, for better or worse, by ordinary users to respond to the needs of ordinary users.  Since Ubuntu seeks out new users, many of those questions are very basic. 

If your developers are looking for support from other developers, they are unlikely to find it here.  Linux developers, regardless of distributions, typically do not frequent user forums. They're more likely to be found on irc, mail lists, bugzillas, etc.

The simplest way to buy into that support package might be  to buy the 5-seat package and eat the cost.

---

### Post by philinux on 2013-12-15
> **msekkappan said:**
> Two of our developers are using ubuntu, and we wouhthttp like to buy the support package for them because they are new to Ubuntu.  When our procurement called, they were told that we can't purchase support for 2 instances.  It has to be 5 or more.  Also, we were told to obtain free help by posting to the forums.  We are not getting satisfactory answers when we post to the forums.

Any ideas???

We are all volunteers here. 

You can also try on freenode irc channel #ubuntu also at askubuntu.com and at 
[http://discourse.ubuntu.com/](http://discourse.ubuntu.com/)

---

### Post by 1clue on 2013-12-15
What languages are your developers working with?  What tools, etc?

I'm a developer too, and I just don't ask development questions on Ubuntu.  Go to the appropriate forum for whatever tool you're having problems with.  I use primarily grails and groovy, which has a mailing list for that sort of thing.  I also occasionally have trouble with virtualization (which I might ask questions about here, since they have a subforum for it, or I might go to the KVM forum and get better answers) or some other tool.

Basic Linux questions you're fine to ask about here.  Basic shell scripts, you might ask here.

Most of the Open Source languages also have really good online documentation, and sometimes a book.  The book is likely to be outdated a bit, but will likely have gems in it that make it easily worth buying and reading.

---

### Post by howefield on 2013-12-15
> **msekkappan said:**
> We are not getting satisfactory answers when we post to the forums.

Any ideas???

If your other posts are indicative of "not getting satisfactory answers" perhaps you need to look at the quality of the questions. Hope you don't think I'm having a go, just saying the better the question, the more likely you are to get help, also feel free to "bump" your post back up the top of the pile once every 24 hours, sometimes those who can help aren't online when you post the question. 

[http://ubuntuforums.org/showthread.php?t=2158945](http://ubuntuforums.org/showthread.php?t=2158945)

---

### Post by msekkappan on 2013-12-16
We have several Windows VMs hosted on Ubuntu OS.  

We do not ask development questions, most questions are related to Ubuntu configurations/issues.  For example, our machine crash every time we close the laptop lid or attach a new monitor to it.  One might think why not search the blogs, support pages etc. to find a solution.  But, we are not trying to become expert in Linux or Ubuntu, we just want someone to help us solve the immediate problem.  Our focus is on development, not configuration of the machines.

---

### Post by msekkappan on 2013-12-16
ok

---

### Post by 1clue on 2013-12-16
Do you have as much swap as you have RAM?  It might be trying to suspend to disk when you close the lid, and it does that to a single swap partition.

---

### Post by msekkappan on 2013-12-16
I just checked the system monitor. the system is using 1.8 GB out of 32 GB memory and 7.92 GB out of 16 GB swap.  You seem to suggest to increase the Swap, I will try.  I never done it, so I am searching for guidance on the web.

BTW, for some reason the system monitor does not seem to include the resource usages of the VMs.  But, the synonyms are the same regardless of whether I have the VMs running or not.  Opening the lid crashes (freezes) the system as well.  I think it is more of a display driver issue, but we have tried this on various types of monitors.  It happens in all.  I haven't tried the lid without connecting the monitor which I am planning to try when I log off today.

---

### Post by 1clue on 2013-12-16
What I mean is that at least one swap partition needs to be as big as RAM or suspending to disk won't work.  As in, can cause a crash.

When you open/close the lid, do you intend to sleep the machine or just get the lid out of the way?

I'm afraid I'm not using a pure Ubuntu, so I don't really know much about system monitor.

---

### Post by vasa1 on 2013-12-17
> **msekkappan said:**
> I just checked the system monitor. the system is using 1.8 GB out of 32 GB memory and 7.92 GB out of 16 GB swap. ...
How does this happen? Can anyone explain why swap is being used when only **1.8 GB out of 32 GB** memory is used?

---

### Post by msekkappan on 2013-12-17
I close the lid because I do not need the laptop display any more.  I have the laptop attached to a monitor.

---

### Post by 1clue on 2013-12-17
You should be able to disable the suspend/hibernate features somehow, but frankly I don't know how.  There's  kernel option, that's a bit extreme.  Never tried to do it software-wise.

---

### Post by bashiergui on 2013-12-17
If you're looking for immediate solutions to problems rather than becoming linux experts, then it seems the obvious solution to the suspend problem is this: don't close the lid. Power off instead or leave the laptop open.

---

