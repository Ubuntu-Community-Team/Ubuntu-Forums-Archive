---
title: "Consistently High Processor Load? - Firefox, GNOME?"
date: 2008-05-05
forum: General Help
---

### Post by igfud on 2008-05-05
Hello,

I upgraded to 8.04 the day it was released.  Since then, I've noticed a much higher processor load while my computer is idling, versus 7.10.  It seems to hover around 40-50% processor load with just Firefox running and one simple web page loaded.  If I go to the processes tab of my System Monitor and sort the processes by CPU load, the values do not add up to the consistent 40-50% load.  "gnome-system-monitor" runs anywhere from 5-20% of the CPU, and Firefox is about 3% on average.

Does this load seem abnormally high to anyone, considering the computer is essentially idling?  The computer is a laptop with a 1.7GHz Pentium M processor.  In Ubuntu 7.10 the fan came on maybe once.  Now it is almost always on.  I keep the computer on one of those Targus chill pads.

Also, sometimes while using Firefox the hard drive LED lights up for 30 seconds or so as if I'm saving a very large file.  Firefox becomes unresponsive during this period (the window grays out), and then once the computer has finished accessing the hard drive Firefox will again become responsive.  This might happen five times in one hour on one day, and not at all the next.

Below I've included a screenshot of my System Monitor:
[IMG]http://linuxham.googlepages.com/cpu.png[/IMG]

Thanks!
igfud

---

### Post by airwolf on 2008-05-05
Disable Firefox checking for attack sites and suspected forgery sites in Preferences -> Security.

Close Firefox and delete ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite

That should do the trick.

---

### Post by sdennie on 2008-05-05
As for the load while under idle.  See this post: [http://ubuntuforums.org/showthread.php?p=4826085](http://ubuntuforums.org/showthread.php?p=4826085)

---

### Post by igfud on 2008-05-06
> Disable Firefox checking for attack sites and suspected forgery sites in Preferences -> Security.

Close Firefox and delete ~/.mozilla/firefox/[profile].default/urlclassifier*.sqlite

That should do the trick. 

That seemed to help quite a bit with Firefox, even speeding the browser up in general.  Thanks!

> As for the load while under idle. See this post: [http://ubuntuforums.org/showthread.php?p=4826085](http://ubuntuforums.org/showthread.php?p=4826085)

Right before I viewed the thread this morning, I was wondering if this might be the problem.  It is.  If I switch from the "Resources" tab (with the live graphs) to the "Processes" tab for 20 seconds or so, and then switch back, the graph dips down quite a bit during that interval.

I went ahead and installed htop, and the the CPU load seems to be a lot more realistic.  It does show that 170 "tasks" are running (this was while Firefox was open).  Does this seem reasonable?  I'm not sure what a task technically refers to, as a lot of programs seem to be running several tasks.

[IMG]http://linuxham.googlepages.com/htop.png[/IMG]

igfud

---

