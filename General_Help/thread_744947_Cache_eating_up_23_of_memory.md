---
title: "Cache eating up 2/3 of memory"
date: 2008-04-04
forum: General Help
---

### Post by tomcat2007 on 2008-04-04
I have noticed that when listening to MP3s, after a dozen tracks or so, I can no longer display file system contents.  When using the wall paper drapes, it crashes, so now I kill it beforehand but that hasn't resolved the problem so I started investigating further.  When looking at program load, only 33% of 2GB of RAM is used and it wasn't until I put the system monitor mini-graphs on the taskbar that I noticed that 66% of the 2 gigs is being used as cache... but cache for what?  This memory consumption doesn't show on the system monitor applet.

Seems that even without listening to music, the system is hovering at about 32% & 62% so resources are almost exhausted then.  After booting, it starts crawling upward, the longer the system sits, whether idle or not.

Am running 32 bit Gutsy on an HP Pavilion dv9000z, AMD64x2 2.0GHz, 2GB RAM, and it doesn't at a cursory glance appear to be under a heavy load.  Typically, have only a few windows at a time.

This is a hell of a memory leak... is there a configuration setting to limit the amount of memory that is allowed to be reserved for cache or some other kind of fix to get around this?  Thanks!

---

### Post by TidusBlade on 2008-04-04
Yeah thats what Linux is doing with the extra RAM you got. You have 2GB RAM, why only use like 750MB of RAM, when the system can take advantage of the other 66% for cache?
I think it makes your system faster and such things, but anyways, if application memory needs more, cache will shrink for application memory ;)

Not exactly sure on the first problem but it could be Compiz if you have it installed.

---

### Post by bmac on 2008-04-04
Look at your "Adminstration" "System Monitor" /  "Processes" tab and you may be able to identify a process that's devouring you available memory and potential CPU %.

---

### Post by tomcat2007 on 2008-04-04
Thanks for the replies :-)

Compiz-fusion is installed but CPU utilization isn't abnormally high.  Gnome-system-monitor checks in at 5-25% with the average around 10%.  Xorg runs from 2-5%.  Compiz-real sits at 1% and everything else is flatlined 99% of the time.  CPU utilization scales to 800MHz on both cores unless Gnome-system-monitor is spiking at 25%.

Firefox is the only thing using a great deal of memory, it's hit as high as 150MB so I make a habit of killing & restarting once a day.  Right now the memory hogs are Firefox@60MB, Vidalia@33, Nautilus@31, Compiz-real@22, Gnome-panel@18, Nautilus@11, and Tor@10.

When app+cache=99+ if I kill firefox & restart, I can then browse other directories in Nautilus which is why I feel that if I am able to exert some manual control over the cache, it would prevent the problem mentioned in the OP from occurring during music play.  Is there a way to limit cache?  1 gig seems like a reasonable ceiling with my configuration, does it not (if I could manually configure this value).

---

### Post by bmac on 2008-04-05
What is your cache setting in Firefox? "Edit" "Preferences" "Advanced" "Network"

---

### Post by dcstar on 2008-04-05
> **bmac said:**
> What is your cache setting in Firefox? "Edit" "Preferences" "Advanced" "Network"

Irrelevant, that is a Disk Cache value and has nothing to do with memory.

---

### Post by mcduck on 2008-04-05
Having all free RAM used as cache for disk reads/writes doesn't limit available memory in any way, and shouldn't cause any problems. It's normal, and the way memory should be managed in Linux. RAM not used is RAM wasted. (So it's not a memory leak, it's just Linux using your hardware to it's full potential).

Unless you have some hardware problem with your RAM, it's not likely that this behavior would be the reason for your problems. If it was, we all would be suffering from the same issues.

If you really believe that your problems are related to memory usage I suggest running the memtest from the Grub menu, at least over night, to make sure your RAM isn't defect. After that I recommend trying without Compiz, Tor and Vidalia.

---

### Post by tomcat2007 on 2008-04-05
Thanks for the advice, McDuck.  Already performed an intensive memory test, nothing wrong there.  I'll invest some time profiling those programs and perhaps others if those don't appear to be the culprit.

Perhaps it would be a good idea to keep Tor, Privoxy, & Vidalia shut down anyway unless I'm using them (which really isn't too often) so I'll whip out a couple scripts for that.  I'm not at my laptop at present, but I'm fairly sure none of those programs have reached 1.0 yet and Tor has had some memory leakage issues in the past.

---

