---
title: "pypanel won't start"
date: 2007-08-20
forum: General Help
---

### Post by tronica on 2007-08-20
Im running openbox, and i installed pypanel, how ever if i start it from the terminal, i get a bunch of errors,

> tronica@desktop:~$ pypanel
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 957, in <module>
    PyPanel(display.Display())
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 80, in __init__
    self.display = _BaseDisplay(display)
  File "/var/lib/python-support/python2.5/Xlib/display.py", line 67, in __init__
    apply(protocol.display.Display.__init__, (self, ) + args, keys)
  File "/var/lib/python-support/python2.5/Xlib/protocol/display.py", line 124, in __init__
    self.default_screen = min(self.default_screen, len(self.info.roots) - 1)
  File "/var/lib/python-support/python2.5/Xlib/protocol/rq.py", line 1371, in __getattr__
    raise AttributeError(attr)
AttributeError: roots
tronica@desktop:~$

is there anything i can do to get it to work?

---

### Post by tronica on 2007-08-20
nevermind i found a fix.

> First, open up (as root) the file /var/lib/python-support/python2.5/Xlib/protocol/display.py and search for the following line:

recv = self.socket.recv(2048 )

Change the 2048 for 4096 (double of it), save the file

---

