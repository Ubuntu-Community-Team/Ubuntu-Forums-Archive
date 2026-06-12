---
title: "cpu frequency indicator fails"
date: 2012-11-15
forum: General Help
---

### Post by ELD on 2012-11-15
Any idea why?

> liam@liam-desktop:~$ indicator-cpufreq
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 81, in <module>
    ind = MyIndicator()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 95, in __init__
    self.update_ui()
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/indicator.py", line 106, in update_ui
    fmin, fmax, governor = cpufreq.get_policy(self.cpus[0])
  File "/usr/lib/python2.7/dist-packages/indicator_cpufreq/cpufreq.py", line 143, in get_policy
    policy = (p.contents.min, p.contents.max, p.contents.governor)
ValueError: NULL pointer access


---

### Post by mc4man on 2012-11-15
The indicator has no issue here
Does this have any relevance to you (exact same error), caused by "turning off speedstep in the BIOS"

[https://bugs.launchpad.net/indicator-cpufreq/+bug/931583](https://bugs.launchpad.net/indicator-cpufreq/+bug/931583)

---

### Post by pqwoerituytrueiwoq on 2012-11-15
my guess is the script is trying to access a api in the panel that is not accessible while running directly from a terminal

---

