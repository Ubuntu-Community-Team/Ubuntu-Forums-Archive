---
title: "Emacs and Python"
date: 2004-10-30
forum: General Help
---

### Post by trico on 2004-10-30
I want write a small python script using emacs but emacs is not recognizing the python extension (it remains in the fundamental mode).  Looking around in /usr/share, I see emacs (and emacs21).  Looking in /etc/emacs I see *.el files refering to python.  I suppose I'm missing some configuration element for emacs.  Can someone point me in the right direction?

Trico

Addendum: I decided that I may not have the right python files and went looking.  Found python-mode.el on sourcefoge and downloaded it.  Now trying to figure out where it goes...

---

### Post by robban on 2004-10-31
apt-get install python-mode should do the trick.
Good luck..

Update: You might have to do "sudo apt-get install python-mode",
if you use the default settings.

---

### Post by trico on 2004-10-31
That did it.  Thanks.

Trico

---

