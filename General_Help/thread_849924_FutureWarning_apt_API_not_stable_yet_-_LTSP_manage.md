---
title: "FutureWarning: apt API not stable yet - LTSP manager not working"
date: 2008-07-05
forum: General Help
---

### Post by Avinash.Rao on 2008-07-05
Below is the error when i execute ltsp-manager as root or any user.
The keyboard interrupt is when i press ctrl-c in the terminal. Otherwise i have a blank windows with a heading ltsp-manager and nothing happens.

Please help!

/usr/lib/python2.5/site-packages/apt/__init__.py:18: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Traceback (most recent call last):
  File "/usr/bin/ltsp-manager", line 255, in <module>
    base.main()
  File "/usr/bin/ltsp-manager", line 251, in main
    gtk.main()
KeyboardInterrupt

---

### Post by Avinash.Rao on 2008-07-06
:) :confused:

---

### Post by Avinash.Rao on 2008-07-06
I guess i will report this as a bug!!
:(

---

