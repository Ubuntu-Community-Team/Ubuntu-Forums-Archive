---
title: "problem running startup-manager"
date: 2007-12-15
forum: General Help
---

### Post by din on 2007-12-15
hi

startup-manager wont open
tried from terminal : 
 sudo gksu -k /usr/bin/startupmanager
Traceback (most recent call last):
  File "/usr/bin/startupmanager", line 20, in <module>
    import startupmanager
  File "/usr/lib/python2.5/site-packages/startupmanager/__init__.py", line 1, in <module>
    from startupmanager.gtk_frontend import SumGui
  File "/usr/lib/python2.5/site-packages/startupmanager/gtk_frontend.py", line 28, in <module>
    import gnome.ui
  File "/var/lib/python-support/python2.5/gtk-2.0/gnome/__init__.py", line 13, in <module>
    from _gnome import *
ImportError: /usr/lib/libasound.so.2: undefined symbol: midiparser_input_buf

any ideas?
.

---

### Post by Jimmy_r on 2007-12-15
Hm, this is not a bug in startup-manager, it goes deeper.
I can not offer much help.
I found these two links from googling the ImportError line though:

[http://www.4front-tech.com/forum/viewtopic.php?t=2273&sid=bb09619de0c16f1b9a2128adea4c6008](http://www.4front-tech.com/forum/viewtopic.php?t=2273&sid=bb09619de0c16f1b9a2128adea4c6008)
[http://ubuntuforums.org/showthread.php?t=541309](http://ubuntuforums.org/showthread.php?t=541309)

---

### Post by din on 2007-12-15
Thank you anyway. i will check this links.
And i think it happend after installing OSS and removing alsa drivers,
that didnt worked anyway for me.

---

### Post by nfm on 2008-03-01
OSS is the reason, all GNOME apps try to load libasound.so.2 which they're unable when OSS is installed. Run your program from terminal and you'll see the errors. Dirty way to fix this would be to:
```
sudo mv /usr/lib/libasound.so.2 /usr/lib/libasound.so.2.bak
ldconfig
```

---

### Post by janfsd on 2008-03-02
A better way is:
```
sudo apt-get install libesd0
```
OSSv4 is great!

---

