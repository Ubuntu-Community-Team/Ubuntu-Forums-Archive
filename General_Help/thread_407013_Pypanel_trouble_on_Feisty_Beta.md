---
title: "Pypanel trouble on Feisty Beta"
date: 2007-04-11
forum: General Help
---

### Post by justin on 2007-04-11
When trying to run pypanel, I get the following errors:

justin@rain:~$ pypanel
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

Any suggestions?

---

### Post by grte on 2007-04-11
Pypanel doesn't like python2.5.

Use this:

```
python2.4 /usr/bin/pypanel
```

Assuming you have python2.4 installed, at any rate.

---

### Post by justin on 2007-04-12
justin@rain:~$ python2.4 /usr/bin/pypanel
Traceback (most recent call last):
  File "/usr/bin/pypanel", line 892, in ?
    from ppmodule import ppinit, ppshade, ppicon, ppfont, ppfontsize, ppclear
ImportError: No module named ppmodule

Now what :(

---

### Post by josevitor on 2007-05-16
[http://blog.ogmaciel.com/?p=248](http://blog.ogmaciel.com/?p=248)

---

### Post by ardya on 2007-05-25
Nn habla...is there an English translation or a fix?

---

