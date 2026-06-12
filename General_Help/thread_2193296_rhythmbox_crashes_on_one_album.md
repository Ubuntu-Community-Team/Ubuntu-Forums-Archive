---
title: "rhythmbox crashes on one album"
date: 2013-12-12
forum: General Help
---

### Post by ELD on 2013-12-12
For some reason rhythmbox crashes on this one album on every first run, closing and re-opening gets it to work, here's the terminal output:
> liam@liam-ubuntu:~$ rhythmbox


(rhythmbox:2606): Gtk-WARNING **: Theme file for DMZ-Black has no directories




(rhythmbox:2606): Gtk-WARNING **: Theme file for DMZ-Black has no directories




(rhythmbox:2606): GLib-GObject-CRITICAL **: Custom constructor for class SoupServer returned NULL (which is invalid).  Unable to remove object from construction_objects list, so memory was probably just leaked.  Please use GInitable instead.
Unable to open ~/.mtpz-data for reading, MTPZ disabled.Traceback (most recent call last):
  File "/usr/lib/rhythmbox/plugins/artsearch/embedded.py", line 38, in discovered_cb
    (found, sample) = tags.get_sample(tagname)
AttributeError: 'NoneType' object has no attribute 'get_sample'


Then it just stays there, any idea why? :(

---

