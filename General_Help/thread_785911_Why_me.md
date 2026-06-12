---
title: "Why me?"
date: 2008-05-07
forum: General Help
---

### Post by Drone4four on 2008-05-07
Compiz impressively loads automagically on the Ubuntu Hardy LiveCD on a 1.7Ghz celeron (from 2002).  However, while idle, gnome-system monitor tells me that it takes up 100% CPU usage. So I turned compiz off.  Even with compiz turned off, gnome-system-monitor tells me X.org is consistently taking up 40% CPU usage while idle.  I close gnome-system-monitor, and top tells me  the CPU is consistently 99% idle.  And why must gnome-system-monitor take up so much CPU usage? Why me?  Or, perhaps a more fair and constructive question is what can I do to help the Ubuntu or Gnome development teams to optimize gnome-system-monitor for their next releases?

---

### Post by zmjjmz on 2008-05-07
Actually, a better idea would be to use conky instead of gnome-system-monitor.

---

### Post by Drone4four on 2008-05-07
Conky is hard for me to configure because its by text editor rather than a neatly organized GUI.

---

### Post by zmjjmz on 2008-05-07
The syntax is pretty logical, and there's a whole thread devoted to conky setups that you could grab a few configuration files from.

---

### Post by cardinals_fan on 2008-05-07
> **Drone4four said:**
> Conky is hard for me to configure because its by text editor rather than a neatly organized GUI.
I would say it the other way around :)

---

### Post by 23meg on 2008-05-07
[QUOTE=Drone4four]And why must gnome-system-monitor take up so much CPU usage? Why me? Or, perhaps a more fair and constructive question is what can I do to help the Ubuntu or Gnome development teams to optimize gnome-system-monitor for their next releases?[/QUOTE]

There's a fix in hardy-proposed now; enable it and help with testing.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)

---

### Post by original_jamingrit on 2008-05-07
> **Drone4four said:**
> Conky is hard for me to configure because its by text editor rather than a neatly organized GUI.

[http://ubuntuforums.org/showthread.php?t=281865&highlight=conky](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

Check the above thread for conky scripts people have made, maybe you'll find one you like.

---

### Post by Tundro Walker on 2008-05-08
If you don't like text-editing config files, then just stick with Gnome System Monitor.  It's a bit CPU intensive, because it's refreshing constantly.  You can turn down how often it refreshes in the preferences.

---

### Post by akiratheoni on 2008-05-08
I normally steal someone else's .conkyrc then just tinker with it a little :) It's actually not as hard as you think. It's intimidating at first but in reality really, really easy.

---

### Post by erfahren on 2008-05-08
In case anyone's interested there's also [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") - I don't know much about it but it has been around awhile. Search Synaptic Package Manager for it - there are other plugins listed in there for it as well.

It may be easier to configure than Conky

---

### Post by akiratheoni on 2008-05-08
Oh, I've used GKrellM before. I don't remember much as I used it back in Dapper but I remember that I liked having the system display stats (it was the first one I used) but I wasn't a fan of GKrellM.

---

### Post by Drone4four on 2008-05-08
> **23meg said:**
> There's a fix in hardy-proposed now; enable it and help with testing.
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)
Thanks, this is what I was looking for. I can't promise I'll test, but it looks like this bug will get squashed given all the attention it is getting by  people.  I am glad to see there is already a good bug report  on this extremely problematic and intrusive bug in gnome-system-monitor. 

> **cardinals_fan said:**
> I would say it the other way around :)What's the other way around?  What are you talking about cardinals_fan?

> **akiratheoni said:**
> I normally steal someone else's .conkyrc then just tinker with it a little :) It's actually not as hard as you think. It's intimidating at first but in reality really, really easy.akiratheoni: see my response to zmjjmz below.

> **zmjjmz said:**
> The syntax is pretty logical, and there's a whole thread devoted to conky setups that you could grab a few configuration files from. Yes, I found this thread.  I tried about a half dozen differnt scripts.  Each one gave me dependency errors.  I tried modifying the lines which are indicated by key terms in the error message.  Selecting key terms from the error messages, I'd search them in the .conkyrc  and sometimes there would be no instances of them, leaving me with a script that won't load.  In fact, not a single script works except the ugly uninformative default one.

> **erfahren said:**
> In case anyone's interested there's also [GKrellM]("http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html") - I don't know much about it but it has been around awhile. Search Synaptic Package Manager for it - there are other plugins listed in there for it as well.

It may be easier to configure than Conky

GKrellM is ugly.  Thanks for the suggestion, though.

By the way, the spell check built into Firefox was a big help as I typed this post.

---

### Post by Drone4four on 2008-05-08
> **23meg said:**
> There's a fix in hardy-proposed now; enable it and help with testing.

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/187383)

Apparently there has been a "Fix Committed."  How can I test the committed fix?

---

### Post by 23meg on 2008-05-08
Enable "Pre-released updates" in System / Administration / Software Sources / Updates, update your gnome-system-monitor package, see if the problem persists, and post your feedback to the bug report.

---

### Post by K.Mandla on 2008-05-08
Moved to Desktop Effects and Customization.

---

