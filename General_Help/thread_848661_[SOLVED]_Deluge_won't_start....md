---
title: "[SOLVED] Deluge won't start..."
date: 2008-07-03
forum: General Help
---

### Post by kamitsukai on 2008-07-03
[FONT="Comic Sans MS"][SIZE="2"]I can't get Deluge to start up! it will just say it's loading and then nothing will happen:confused:

Here's what i get when starting from terminal:[/SIZE][/FONT]
```
dreamsofubuntu@dreamsofubuntu-desktop:~$ deluge
no existing Deluge session
Starting new Deluge session...
Traceback (most recent call last):
  File "/usr/bin/deluge", line 133, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 116, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 54, in __init__
    common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 202, in __init__
    self.config = pref.Preferences(os.path.join(self.base_dir, PREFS_FILENAME))
  File "/var/lib/python-support/python2.5/deluge/pref.py", line 291, in __init__
    self.load(self.config_file)
  File "/var/lib/python-support/python2.5/deluge/pref.py", line 336, in load
    self.dump = pickle.load(pkl_file)
cPickle.UnpicklingError: A load persistent id instruction was encountered,
but no persistent_load function was specified.

```
[FONT="Comic Sans MS"][SIZE="2"]
Thanks in advance[/SIZE][/FONT]

---

### Post by kamitsukai on 2008-07-07
<bump>

---

### Post by carlosroan89 on 2011-10-04
hello

i have the same problem. why does ot say its solved and i dont see any posts.:(

---

### Post by sffvba[e0rt on 2011-10-04
I would suggest starting a new thread and giving as much info (error messages etc.) to assist in fixing it.

Back to sleep old thread...


404

---

