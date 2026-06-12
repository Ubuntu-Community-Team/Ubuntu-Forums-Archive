---
title: "USB Mass Storage problems after 7.10 upgrade"
date: 2007-12-08
forum: General Help
---

### Post by CalonDdraig on 2007-12-08
Hello Guys,

Sorry for this thread being a little technically bland as I dont know which areas to look at here. 

A couple of weeks ago, I upgraded from 7.4 Feisty which had been working well since I upgraded 6.10 - that upgrade process was flawless, but alas the upgrade to 7.10 wasn't. I started the upgrade process, and halfway through something went wrong and the machine froze. I left it on overnight in case it was merely being slow, but to no avail so I eventually had to pull the plug. 

Now I find myself with a system that is best described as a hybrid of 7.10 and 7.4. Everything seems ok though and I'm preforming upgrades from the 7.10 repos. 

However: I have a problem with any device which uses the USB Mass Storage standard. I have a couple of pendrives and an external hard disk and they just aren't working. When I plug them in I get a message that says: "Cannot Mount Volume" and a prompt to try the command "dmesg | tail" command... when I try, all I get is info about the ethernet interface eth0. 

Basically, I was wondering where to start looking to fix this... are there any things that strike as obvious to try? I'm not that good at kernel stuff or modules (I've compiled a fed and modprobed them but that's all) and although I've been googleing, I've not really found anything that's of help.

Any ideas?

CalonDdraig

---

### Post by dcstar on 2007-12-08
> **CalonDdraig said:**
> Hello Guys,

Sorry for this thread being a little technically bland as I dont know which areas to look at here. 

A couple of weeks ago, I upgraded from 7.4 Feisty which had been working well since I upgraded 6.10 - that upgrade process was flawless, but alas the upgrade to 7.10 wasn't. I started the upgrade process, and halfway through something went wrong and the machine froze. I left it on overnight in case it was merely being slow, but to no avail so I eventually had to pull the plug. 

Now I find myself with a system that is best described as a hybrid of 7.10 and 7.4. Everything seems ok though and I'm preforming upgrades from the 7.10 repos. 
...........
Any ideas?

CalonDdraig

You obviously do not have a correctly upgraded system, this is probably the root cause of this problem (and possibly others).

I would suggest resizing you current partition to make room for a full 7.10 install, and then doing a fresh install to ensure that you have a fully operational system.

---

### Post by geirha on 2007-12-08
If it was upgrading packages when it froze, you should be able to finish it with ```
sudo dpkg --configure -a
```

---

