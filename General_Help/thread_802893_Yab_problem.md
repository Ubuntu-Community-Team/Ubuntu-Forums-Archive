---
title: "Yab problem"
date: 2008-05-21
forum: General Help
---

### Post by Sordelka on 2008-05-21
Hi, I installed adesklets correctly.

When trying to launch yab.py it says:

Now testing...
============================================================
If you do not see anything (or just an initial flicker
in the top left corner of your screen), try `--help',
and see the FAQ: `info adesklets'.
============================================================
Traceback (most recent call last):
  File "./yab.py", line 48, in <module>
    import adesklets
  File "/usr/lib/python2.5/site-packages/adesklets/__init__.py", line 43, in <module>
    raise e
adesklets.error_handler.ADESKLETSError: adesklets process exited - 
Exception exceptions.AttributeError: AttributeError("'NoneType' object has no attribute 'kill'",) in <bound method _Communicator.__del__ of <adesklets.communicator._Communicator instance at 0x827af2c>> ignored


Anyone can help me?

---

