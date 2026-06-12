---
title: "Tracker doesn't show results"
date: 2007-10-23
forum: General Help
---

### Post by rudlavibizon on 2007-10-23
Look at this: 

[IMG]http://img129.imageshack.us/img129/6870/screenshottrackersearchsj7.png[/IMG]

---

### Post by rudlavibizon on 2007-10-24
bump

---

### Post by korami on 2007-11-04
This is also occurring to me, but only for certain search items... for others it displays the results ok. I couldn't find a pattern either...

---

### Post by korami on 2007-11-04
This post might bring a workaround for the issue:

[http://ubuntuforums.org/showthread.php?t=583134&highlight=tracker](http://ubuntuforums.org/showthread.php?t=583134&highlight=tracker) .

---

### Post by gmaniac on 2007-11-04
The solution I found to this and other problems was to uninstall tracker and install beagle.

---

### Post by korami on 2007-11-04
That's an alternative indeed, but I'd still like to stick with tracker, since beagle was, at least on my machine, way too resource hug, and I had to kill it in Feisty every time I had to do some stuff that required a bit more ram.

---

### Post by gmaniac on 2007-11-04
Resource hog ? I am using this on 2Ghz 512 Ram computer and I haven't
experienced any problems yet.On idle it has two processes beagled and beagled-helper with ~ 24MB combined memory and cpu usage of 0. Live search is fast. 
If you don't find any other solution and till tracker bugs get fixed there is no harm in trying beagle once more. Just my 5c.

PS. Not just for tracker/beagle, but It might be a good idea to turn on noatime in your fstab!!. Try and search for this.

---

### Post by korami on 2007-11-04
Thanks for your suggestion gmaniac, I might try it out. However, as compared to your values, beagle was eating up 30-50% of the CPU for me, so was no real option.

For now I managed to make tracker working with the 'trackerd -v 2 -R' command. I'll give beagle another try though if I come into new issues with tracker.

---

