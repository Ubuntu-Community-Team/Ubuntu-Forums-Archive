---
title: "python-parallel error: udev's fault?"
date: 2005-09-21
forum: General Help
---

### Post by marco_ on 2005-09-21
I've installed latest hoary and the package python-parallel. If I run this script:

#!/usr/bin/python
import parallel
p=parallel.Parallel()


there is this error:

Traceback (most recent call last):
  File "par-test.py", line 3, in ?
    p=parallel.Parallel()
  File "/usr/lib/python2.4/site-packages/parallel/parallelppdev.py", line 174, in __init__
    self._fd = os.open(self.device, os.O_RDWR)
OSError: [Errno 2] No such file or directory: '/dev/parport0'
Exception exceptions.AttributeError: "Parallel instance has no attribute '_fd'" in <bound method Parallel.__del__ of <parallel.parallelppdev.Parallel instance at 0xb7dffe8c>> ignored


really, there is no /dev/parport0 on my system: is udev's fault?
BTW, some months ago, I've run the *same* script on a debian system (without udev) and it worked.

suggestions? many thanks.
Marco

---

