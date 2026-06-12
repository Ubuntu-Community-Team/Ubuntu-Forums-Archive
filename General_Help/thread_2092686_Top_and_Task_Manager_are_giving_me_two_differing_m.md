---
title: "Top and Task Manager are giving me two differing memory readings (SCREENSHOT)"
date: 2012-12-08
forum: General Help
---

### Post by hmsimha on 2012-12-08
here's a screenshot of what's going on: [[img]http://s16.postimage.org/ejpvywlqd/screenshot_12082012_121053pm.png[/img]](http://postimage.org/image/d4oba6kn5/full/)
[image ru](http://postimage.org/)
According to my task manager, my memory is 37% in use. According to top, it's over 75% utilized. 

Two aside questions: In top, what do the different percentages next to the CPU % indicate? Also, the most I've ever seen my swap file utilized was 10%, after running for several days and with extremely heavy usage. I have my swap set to 3 GB with 2 GB of RAM.. should I reduce it? (I don't care about hibernation if that makes a difference)

Thanks!

---

### Post by Vaphell on 2012-12-08
> what do the different percentages next to the CPU % indicate?

```
Cpu(s):  6.9%us,  1.8%sy,  0.0%ni, 90.7%id,  0.5%wa,  0.0%hi,  0.0%si,  0.0%st
```
these?
user, system, niced, idle etc

[http://linux.die.net/man/1/top](http://linux.die.net/man/1/top)
> The summary area fields describing CPU statistics are abbreviated. They provide information about times spent in: us = user mode sy = system mode ni = low priority user mode (nice) id = idle task wa = I/O waiting hi = servicing IRQs si = servicing soft IRQs st = steal (time given to other DomU instances) 

---

### Post by Kirk Schnable on 2012-12-08
This article may speak to your memory usage question. 

[http://www.chrisjohnston.org/ubuntu/why-on-linux-am-i-seeing-so-much-ram-usage](http://www.chrisjohnston.org/ubuntu/why-on-linux-am-i-seeing-so-much-ram-usage)

---

### Post by hmsimha on 2012-12-08
That was an interesting read. So basically, I am only USING 37% of my RAM but the difference in top is also counting RAM that isn't currently being used but hasn't yet been deallocated as nonfree.

---

### Post by Cheesemill on 2012-12-08
Correct.

Here's another explanation:
[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Kirk Schnable on 2012-12-08
> **hmsimha said:**
> That was an interesting read. So basically, I am only USING 37% of my RAM but the difference in top is also counting RAM that isn't currently being used but hasn't yet been deallocated as nonfree.

Yep!  The graphical task managers will usually not count the cached stuff because they don't want to add to the "Linux ate my RAM" paranoia. And anyway, reporting it that way is still useful and accurate.

---

