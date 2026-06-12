---
title: "help with wifi radar"
date: 2006-09-11
forum: General Help
---

### Post by aoalneowlknsadflkafgibj on 2006-09-11
I installed wifi-radar the other day and its been so awesome. Then suddenly yesterday it stoped working. When I run it from the command line I get this error.

matux@matux-laptop:~$ gksudo -S wifi-radar
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Traceback (most recent call last):
File "/usr/sbin/wifi-radar", line 1896, in ?
import gtk, gobject
File "/usr/lib/python2.4/site-packages/gtk-2.0/gtk/__init__.py", line 45, in ? from _gtk import *
RuntimeError: could not open display



I searched these fourms already and found another thread with the same problem but it didnt help solve my problem. Any ideas?

---

