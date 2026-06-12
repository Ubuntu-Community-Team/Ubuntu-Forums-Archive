---
title: "HP M1212 3 in 1 stopped scanning"
date: 2020-01-14
forum: General Help
---

### Post by mrkeef on 2020-01-14
Back in October I performed an upgrade from 19.04 to 19.10.

Since then I have been unable to scan on my HP 3 in one (USB connected)

From hp-setup I get this:
> Traceback (most recent call last):
  File "/usr/bin/hp-setup", line 48, in <module>
    from base import device, utils, tui, models, module, services, os_utils
  File "/usr/share/hplip/base/device.py", line 42, in <module>
    from . import status
  File "/usr/share/hplip/base/status.py", line 33, in <module>
    import cupsext
ImportError: libhpipp.so.0: failed to map segment from shared object

It prints without any problem.

Simple scan finds it as a scanner but will not actually connect to it when I presss "Scan".

---

### Post by mörgæs on 2020-01-15
That's a long time waiting. Have you considered a clean install of 19.10?

---

### Post by mrkeef on 2020-01-28
Not really. It's a bit of a hassle, especially as we are half way to 20.4 :)

---

