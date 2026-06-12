---
title: "Evolution crashing problems"
date: 2006-10-30
forum: General Help
---

### Post by toMeloos on 2006-10-30
Evolution was never the most stable program of the Gnome desktop, but since upgrading to Edgy it crashes all the time.

Every few hours my system locks up. All RAM and swap space become filled, there is non-stop hard diks activity and the system load goes up to about 19 or more. By the time this stops (takes several minutes), evolution is gone and often other programs (some applets, gaim etc.) were dragged along with it, probably due to a shortage of memory.

Reducing vm.swappiness from 60 to 10 has improved the situation somewhat, because with the slow hard disk of my laptop extensive usage of swap makes the system unuseable. Load goes through the roof, just because of the swapping activity :( 

The only bug buddy windows I got so far were for those other programs, but never for evolution.

I've got two questions:

1. Given the current behavior, is there a way to generate the nessecary information after the crash to file a decent gnome or ubuntu bug report?

2. Is there a way, other than trying a clean Edgy install or downgrading, to get evolution to run stable?
I hope someone has some suggestions for improvement or read other forum threads/bug reports that resemble this problem.

---

### Post by kasulstyls on 2006-10-31
i too am having the same problem! ](*,)

---

### Post by toMeloos on 2006-10-31
I ran 'sudo dpkg-reconfigure evolution' from the terminal and it looks like my problem might be solved. Evolution used to crash every few hours, and now it hasn't done so in almost a day. Try it.

---

### Post by toMeloos on 2006-11-23
I did a completely clear install of edgy, put my home dir back and evolution still shows the same behavior :( 

Anybody got suggestions on how to prevent this? It's extremely annoying. My laptop is basically unusable and I've got deadlines to meet...

---

### Post by Spin Doctor on 2006-11-28
I am experiencing constant crashes with the Evolution Calender. I would not be exagariting if I say it crashes atleast 5-7 times a day. It seem this module is very unstable. The email module on the other hand, does rarely crash on me. How come these two different modules from the same software suite has such different "crash" behavior? It is very frustrating, and I am surprised Evolution comes with the distro considering its crashintensity...

I like the integration with the OS, but I am feed up with constant crashes with the calender module which I use to sync with my palmpilot.

---

### Post by claypole on 2007-02-05
I am having the same problem.  Evolution just randomly crashes, mainly when I'm not even using it!  Any news? :confused:

---

### Post by Spin Doctor on 2007-02-10
My crashes with evolution mainly comes from the calender module. After I removed the gradient coloring, It feels like Evolution does not crash on me that much anymore. Try it. Let me know if it does reduces number of crashes for you aswell!

In your commandline:     ```
 gconf-editor 
```     [LEFT]Navigate through the treestructure in the left pane to:
[/LEFT]
 **apps > evolution > calender > display**[B]

Uncheck the property, "events_gradient"[/B]

Exit gconf-editor

Restart Evolution

---

### Post by CocoAUS on 2007-02-10
Evolution's been fairly stable for me.  The only two problems I've encountered are 1) the filters didn't work once, and 2) the contacts got blown away once.

Other than that, I love Evolution.  Even more than Thunderbird.

For those of you having problems with Evolution, why don't you try switching to KMail or Thunderbird?  Is it because you need the calendar and contacts integrated?

---

### Post by Spin Doctor on 2007-02-10
For me the integration of the calender, email, tasklists are the main reson I use Evolution. I came from the lightweight Thunderbird before, so it has taken some time getting used to Evolution.

With some tweaking in its settings, I have come to really enjoy using it! Hopefully next version will have some bugs taken care of...

---

