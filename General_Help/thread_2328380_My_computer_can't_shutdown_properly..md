---
title: "My computer can't shutdown properly."
date: 2016-06-20
forum: General Help
---

### Post by duncan7 on 2016-06-20
I recently purchased a dell inspiron 7559 gaming laptop and have wiped the HDD of windows and installed Ubuntu mate on it. (mate keeps crashing so I use cinnamon instead). Every time I press the shut down button. Everything closes and I get a black screen but it doesn&#8217;t power off. After about 20 seconds it prints to the screen an error like this:
[B][SIZE=4]BUG: soft lockup - CPU stuck for 23s
[/SIZE][/B]and continues printing similar error every ~20 second till i hold down the power button

I'm relatively new to Ubuntu and I don't know how to fix this. Any help would be appreciated!

---

### Post by QDR06VV9 on 2016-06-20
I have seen that error before, are you overclocking your CPU? this can be caused by a unstable overclock.
And also a PSU that could be failing or is to small Watt wise.

---

### Post by duncan7 on 2016-06-20
I'm not overclocking. Do you really think its a PSU problem?

---

### Post by RobGoss on 2016-06-20
Hello and welcome to the forum, Have you try other distributions other then Ubuntu mate on this machine? I would say give Ubuntu 16.04 a try and see if you have this same problem

---

### Post by poorguy on 2016-06-20
Perhaps these links will help.

[http://ubuntuforums.org/showthread.php?t=2205211](http://ubuntuforums.org/showthread.php?t=2205211)

[http://ubuntuforums.org/showthread.php?t=2235087](http://ubuntuforums.org/showthread.php?t=2235087)

---

### Post by ventrical on 2016-06-21
> **runrickus said:**
> I have seen that error before, are you overclocking your CPU? this can be caused by a unstable overclock.
And also a PSU that could be failing or is to small Watt wise.

A failing psu will cause a sort of a wait state.  So the shutdown sequence misses the signal.  This is a HID defect common on a lot of hardware. Low watts, but as it tries to recover the wait is locked. It emulates a software bug.

regards..

---

