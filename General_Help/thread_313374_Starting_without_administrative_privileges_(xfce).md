---
title: "Starting without administrative privileges (xfce)"
date: 2006-12-05
forum: General Help
---

### Post by donknotts on 2006-12-05
I've just xubuntu 6.10.  I've been away awhile in with windows...anyway.  When I boot or restart X, I'm told I'm "Starting without Administrative Privileges".  It then proceeds to load all the applications that were open when it last ran correctly.  I can edit, etc. with sudo and those changes save, but xfce remembers nothing like Groundhog Day.

Steps to this point?  Wanted to turn off the tapping on my synaptic touchpad so I got gsynaptics.  Found out that wasn't straight forward so I uninstalled it and followed the advice in the blog re: editing xorg.conf.  I also updates all the packages in Synaptic. When I restarted X, problems started.  All screen fonts were teeny tiny 9 pt.  I got a message about xfce can't find localhost -*Continue Anyway or try Again*--(check /etc/hosts, which I did).  Added my computer name after "localhost" and the first message went away, but it still gives me the admin. privilege deal.  I tried ifdown and ifup for eth0, too.  Also it seems that there is more latency in resolving webpages.  May just be me though.  Any ideas?  Thanks.

---

### Post by donknotts on 2006-12-05
> **donknotts said:**
> I've just xubuntu 6.10.  I've been away awhile in with windows...anyway.  When I boot or restart X, I'm told I'm "Starting without Administrative Privileges".  It then proceeds to load all the applications that were open when it last ran correctly.  I can edit, etc. with sudo and those changes save, but xfce remembers nothing like Groundhog Day.

Steps to this point?  Wanted to turn off the tapping on my synaptic touchpad so I got gsynaptics.  Found out that wasn't straight forward so I uninstalled it and followed the advice in the blog re: editing xorg.conf.  I also updates all the packages in Synaptic. When I restarted X, problems started.  All screen fonts were teeny tiny 9 pt.  I got a message about xfce can't find localhost -*Continue Anyway or try Again*--(check /etc/hosts, which I did).  Added my computer name after "localhost" and the first message went away, but it still gives me the admin. privilege deal.  I tried ifdown and ifup for eth0, too.  Also it seems that there is more latency in resolving webpages.  May just be me though.  Any ideas?  Thanks.

Me again.  I've discovered that the message has to do with synaptic trying to start without root privileges.

But there's still this problem of xfce not remembering any settings and trying to open everything from earlier today...

---

### Post by Megabuntu on 2007-02-08
Have you resolved the issue concerning starting without admin privileges? I have this problem, but none of the other issues you mentioned. I can do sudo and other things, but this window pops up whenever I start my laptop.???:confused:

---

### Post by becari on 2007-02-17
You can easily get rid of that by removing .cache from your home dir

rm -rf /home/`whoami`/.cache

Did it and it worked.

---

### Post by Megabuntu on 2007-02-19
Thanks. I haven't tried it yet, but what exactly does that do?

---

### Post by becari on 2007-02-21
just deletes the .cache dir in your home dir

---

### Post by Megabuntu on 2007-02-22
Thanks! that did it! I understand that removes the cache .dir, but what does that do and why does removing it make the message go away? just trying to understand this OS!:)

---

### Post by moon2js on 2007-03-23
I had the same problem with synaptic popping up (without root privs) at startup and I'm glad to know I can wipe that by deleting the cache.

I can avoid this in the future by not logging out or shutting down before quiting any admin programs, correct?

---

### Post by kerry_s on 2007-03-23
You guys should turn off the auto save session feature. If you want to start a program use the auto start app. In my experience the session saver is nothing but problems.

---

