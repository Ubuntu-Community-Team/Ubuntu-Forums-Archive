---
title: "indicator-cpufreq won't start on Ubuntu 18.04"
date: 2018-08-24
forum: General Help
---

### Post by michael337 on 2018-08-24
After recently upgrading from 16.04, I upgraded to 18.04. Everything went fine, except that I can't use indicator-cpufreq. It crashes shortly after startup. Here is the output when ran on the terminal: ```
/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py:20: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk
/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py:21: PyGIWarning: AppIndicator3 was imported without specifying a version first. Use gi.require_version('AppIndicator3', '0.1') before import to ensure that the right version gets loaded.
  from gi.repository import AppIndicator3 as appindicator
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 79, in <module>
    ind = MyIndicator(options.show_frequency)
  File "/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py", line 99, in __init__
    self.update_ui()
  File "/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py", line 123, in update_ui
    self.select_items[freq].set_active(True)
KeyError: 1271315


```

I'm using an Intel i5 CPU with 4 threads, and two cores on a Thinkpad T410. Thanks!

---

