---
title: "No Desktop"
date: 2016-01-27
forum: General Help
---

### Post by Darth4212 on 2016-01-27
I recently have been using Windows 10 more on my computer than Ubuntu. Yesterday I booted into Ubuntu and when I signed in I had no desktop whatsoever. So I turned off my computer and then went back into Ubuntu and tried other desktop environments but I still have a desktop.

---

### Post by ajgreeny on 2016-01-27
Is this the same machine as in [http://ubuntuforums.org/showthread.php?t=2311477&p=13429934#post13429934](http://ubuntuforums.org/showthread.php?t=2311477&p=13429934#post13429934) ?

If you are going to remove Ubuntu as you say you want, to there is little point in your query as it will be much easier to solve this type of problem when you are seriously going to use the OS.

---

### Post by Darth4212 on 2016-01-28
> [COLOR=#000000]Is this the same machine as in [/COLOR][http://ubuntuforums.org/showthread.p...4#post13429934]("http://ubuntuforums.org/showthread.php?t=2311477&p=13429934#post13429934")[COLOR=#000000] ?[/COLOR]As a matter of fact yes it is the same machine but the fact that i have no desktop is what is causing me to want to no longer dualboot

---

### Post by ajgreeny on 2016-01-28
It may make a lot more sense to solve one problem at a time or this could get confusing if both threads are left open!
If this turns out to be the case, it may be best to temporarily close this thread and leave the discussion in the other open.

However, before that, can you let us know the version of Ubuntu and what hardware this is using, as it may be something as simple as a graphic driver that needs installing or updating.  The more information the better.

---

### Post by Darth4212 on 2016-01-28
15.10 everything is updated I am able to open a terminal window if that helps

---

### Post by ajgreeny on 2016-01-28
What is the output of ```
lspci
```in terminal, please?  That will tell us the graphic card you have, and also the wifi card, but the first is the likely culprit.

---

