---
title: "can not launch meld or terminator because of cairo error"
date: 2024-03-28
forum: General Help
---

### Post by newcfd on 2024-03-28
undefined symbol: cairo_tee_surface_index on Ubuntu 22.04

Tried to reinstall terminator, meld or cairo. No help.

---

### Post by yancek on 2024-03-28
>  Tried to reinstall terminator, meld or cairo.  		

So what happened when you tried the above?  Did you get warning or error messages?  The more details you post the more likely you will get help.

---

### Post by newcfd on 2024-03-28
Thanks for your reply.

When meld or terminator is started, the following messages are displayed:
=====================================================
Traceback (most recent call last):
  File "/usr/bin/meld", line 387, in <module>
    import meld.meldapp
  File "/usr/lib/python3/dist-packages/meld/meldapp.py", line 29, in <module>
    import meld.ui.util
  File "/usr/lib/python3/dist-packages/meld/ui/util.py", line 20, in <module>
    from meld.ui import gladesupport  # noqa: F401
  File "/usr/lib/python3/dist-packages/meld/ui/gladesupport.py", line 7, in <module>
    from meld import diffmap  # noqa: F401
  File "/usr/lib/python3/dist-packages/meld/diffmap.py", line 19, in <module>
    import cairo
  File "/usr/lib/python3/dist-packages/cairo/__init__.py", line 1, in <module>
    from ._cairo import *  # noqa: F401,F403
ImportError: /usr/lib/python3/dist-packages/cairo/_cairo.cpython-310-x86_64-linux-gnu.so: undefined symbol: cairo_tee_surface_index

---

### Post by newcfd on 2024-04-02
nobody knows the solutions?

---

