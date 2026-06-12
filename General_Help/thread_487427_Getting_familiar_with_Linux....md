---
title: "Getting familiar with Linux..."
date: 2007-06-29
forum: General Help
---

### Post by green_earth on 2007-06-29
Hello Friends,

Now that I'm working and liking ubuntu, I find myself wanting to understand things under the cover better. I'm quite comfortable now with WindowsXP ... keeping it tidy (sort-of) and spyware and virus free (sort-of). Anyway, I want to know how to keep ubuntu running good for  a long time. Right now (two weeks old) its running great on my 4-year old laptop. I don't think it ran this good when it was new (feels fast!). Anyway, how do I keep it running fast and smooth? I like to tinker, and in Windows I have to re-format around once per year to get that fast feeling back in my OS. How can I avoid this with ubuntu?

---

### Post by tnseditor on 2007-06-29
You can run:
Sudo apt-get autoclean
to clean up any unneeded files.  You could always use synaptic to take out packages you may not use.

---

### Post by avik on 2007-06-29
Unilke Windows, Linux doesn't "slow down" over time, at least not in my experience.  So don't worry about it! :)

---

### Post by MCSE_Crossover on 2007-06-29
Yeah, autoclean will really just clean out all of the packages that you have downloaded and installed and are no longer using. Other than that you can just uninstall unneeded programs. But as avik said, it doesn't slow down.

---

### Post by Pheodax on 2007-06-29
Windows XP becomes slow after about 3 days here. I have used Ubuntu (first time Linux-only setup) for 2 weeks now and it's as fast as it was right after installation.

Thank you, Ubuntu-team! ;) :D

---

### Post by MCSE_Crossover on 2007-06-29
Glad things are working out for you!

---

### Post by xspazxd on 2007-06-29
I was wondering this myself, I'm glad its that easy.

---

### Post by nick_h on 2007-06-29
This link may be useful - [HowTo: Cleaning up all those unnecessary junk files...](http://doc.gwos.org/index.php/RemoveJunkFiles).

---

### Post by green_earth on 2007-06-30
I appreciate the responses. Indeed I've not noticed anything at all strange yet in my ubuntu experience. It has been rock stable. Its amazing to me that the only time anything "buggy" has occurred was when Amarok froze the whole system for about 10-15 seconds once when I was trying to add music to the queue. I mean come on, windows media player never does that!;)

For the sake of knowing, if I at some time mess things up, is there a way to get in a try to clean things up? An equivalent to windows safe mode?

---

### Post by Tomosaur on 2007-06-30
> **green_earth said:**
> I appreciate the responses. Indeed I've not noticed anything at all strange yet in my ubuntu experience. It has been rock stable. Its amazing to me that the only time anything "buggy" has occurred was when Amarok froze the whole system for about 10-15 seconds once when I was trying to add music to the queue. I mean come on, windows media player never does that!;)

For the sake of knowing, if I at some time mess things up, is there a way to get in a try to clean things up? An equivalent to windows safe mode?

When you boot your machine, you will see the Grub menu asking you to select an OS to boot into. Normally, the second option is a recovery mode. Booting into this will land you in a root terminal (ie, no GUI), and from there you can clean everything up.

---

### Post by Tmi on 2007-06-30
> **green_earth said:**
> Its amazing to me that the only time anything "buggy" has occurred was when Amarok froze the whole system for about 10-15 seconds once when I was trying to add music to the queue. I mean come on, windows media player never does that!;)

You sure it was a whole system freeze? For me Amarok freezes almost everytime when I start it and it loads the whole playlist and such, but none of my other programs freeze while this happens.

I guess other KDE apps might freeze since they share stuff, but I mostly use gnome apps so I'm not sure.

---

