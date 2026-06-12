---
title: "skype-wrapper error no module named gi.repository"
date: 2013-05-04
forum: General Help
---

### Post by chewy84 on 2013-05-04
I've been trying to link skype with pidgin which i done but now i wanted to get the skype icon in the message bar or what ever its called.

I downloaded the Skype-Wrapper the ppa and that when running skype-wrapper from a terminal this is what i get

Traceback (most recent call last): File "indicator-applet-skype.py", line 34, in import helpers File "/usr/share/skype-wrapper/helpers.py", line 32, in import settings File "/usr/share/skype-wrapper/settings.py", line 30, in from gi.repository import Gio ImportError: No module named gi.repository

I've also been looking for ways to fix this but i'm going around in circulars getting no where any help would be highly appreciated

---

### Post by chewy84 on 2013-05-04
python-gi and python3-gi are both installed and i reinstalled them as well still the same problem.

I'm totally lost on this one, i hope someone can help

---

