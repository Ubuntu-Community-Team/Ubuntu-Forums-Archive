---
title: "LUbuntu noble 24.04 not start show indicator-cpufreq"
date: 2024-06-12
forum: General Help
---

### Post by aug7744 on 2024-06-12
Thanks for reading.

OS Lubuntu (Ubuntu using LXQT) Noble 24.04.
Both cpufrequtils and indicator-cpufreq installed from Ubuntu repository.
cpufrequtils works, but indicator-cpufreq not works.

indicator-cpufreq not start and not show icon in systray.
Trying run "indicator-cpufreq" in terminal show error message

user@1:/$ indicator-cpufreq
Traceback (most recent call last):
  File "/usr/bin/indicator-cpufreq", line 85, in <module>
    ind = MyIndicator(options.show_frequency)
          ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py", line 78, in __init__
    menu_item = Gtk.RadioMenuItem.new_with_label(group, readable_frequency(freq))
                                                        ^^^^^^^^^^^^^^^^^^^^^^^^
  File "/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py", line 34, in readable_frequency
    label = _("%s GHz") % locale.format(_("%.2f"), f / 1.0e6)
                          ^^^^^^^^^^^^^
AttributeError: module 'locale' has no attribute 'format'. Did you mean: '_format'?



====
Have any solution to fix it ?
Have another software to change cpu power profile as being an software loaded in systray using icon ?

Have an nice week.

---

### Post by aug7744 on 2024-06-12
THE SOLUTION
edit in
/usr/lib/python3/dist-packages/indicator_cpufreq/indicator.py
changing in line 34
readable_frequency
    label = _("%s GHz") % locale.format(_("%.2f"), f / 1.0e6)
to
readable_frequency
    label = _("%s GHz") % locale.format_string(_("%.2f"), f / 1.0e6)

[https://bugs.launchpad.net/ubuntu/+source/indicator-cpufreq/+bug/2063547](https://bugs.launchpad.net/ubuntu/+source/indicator-cpufreq/+bug/2063547)

---

### Post by ActionParsnip on 2024-06-13
Will that be rolled back in package updates and so on? I'm guessing a later update will have this change. If not, it'll clobber your efforts

---

