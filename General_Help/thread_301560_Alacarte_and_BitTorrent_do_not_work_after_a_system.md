---
title: "Alacarte and BitTorrent do not work after a system crash"
date: 2006-11-17
forum: General Help
---

### Post by Homayoon on 2006-11-17
This seems a little stupid, I had to do a cold restart after a system crash and after that I couldn't run BitTorrent again. I tried to find the name of the executable to test it in a terminal and see if there is anything to see that... oops, Alacarte doesn't work either. Any ideas about what is going on? They just do not run. The "Starting BitTorrent" and "Starting Alacarte Menu Editor" appear for a few seconds and then disappear.

---

### Post by Homayoon on 2006-11-17
I finally figured it out and found the source of the problem, but now I have a new one. The problem was with the python interpreter that I had messed with recently, and it was nothing about the crash.

I have two versions of python on my machine (2.4 and 2.5). I installed 2.4 from synaptic while I compiled 2.5 from source. I then installed stackless (on 2.5), then I installed wxPython on 2.4 and then I compiled wxPython 2.7 and installed it on python 2.5, then I removed it and installed wxPython 2.6 from synaptic (which was installed on python 2.4), I then compiled wxPython 2.6 and installed it on python 2.5. After that I compiled Stackless onto version 2.4 and then replaced the "python" executable in /usr/local/bin with the new version stackless 2.4 executable, and after a while swapped the original file into its place. Finally (in another process of messing) I lost my python2.4 executable and left everything as it was!

I know it is a real mess! To tackle the problem, I just downloaded python 2.4.4 source code and compiled and installed it, but the I still have the problem.

To show one of the error messages, this is what I get when I run "alacarte" in a terminal:
```

Traceback (most recent call last):
  File "/usr/bin/alacarte", line 20, in ?
    from Alacarte.GnomeFront import GnomeFront
  File "/usr/lib/python2.4/site-packages/Alacarte/GnomeFront.py", line 19, in ?
    import os, cgi, thread
  File "/usr/lib/python2.4/cgi.py", line 40, in ?
    import mimetools
  File "/usr/lib/python2.4/mimetools.py", line 6, in ?
    import tempfile
  File "/usr/lib/python2.4/tempfile.py", line 33, in ?
    from random import Random as _Random
  File "/usr/lib/python2.4/random.py", line 44, in ?
    from math import log as _log, exp as _exp, pi as _pi, e as _e
ImportError: /usr/lib/python2.4/lib-dynload/math.so: undefined symbol: PyFPE_jbuf

```

I really don't know how I can fix all the mess I did! Any ideas?

---

