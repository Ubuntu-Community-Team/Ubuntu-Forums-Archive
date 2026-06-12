---
title: "kabikaboo won't work."
date: 2013-05-21
forum: General Help
---

### Post by t0p on 2013-05-21
Kabikaboo just won't work.  Try it through the GUI (the "Dash") and nothing at all seems to happen.  Try through command line and I get this:

```
t0p@mars:~$ /usr/bin/kabikaboo
Improper shutdown detected...
Traceback (most recent call last):
  File "/usr/share/kabikaboo/src/kabikaboo.py", line 3176, in <module>
    editor.initialize_interface()
  File "/usr/share/kabikaboo/src/kabikaboo.py", line 65, in initialize_interface
    self.open_file_on_startup()
  File "/usr/share/kabikaboo/src/kabikaboo.py", line 1203, in open_file_on_startup
    file_opened, opened_document = self.file.open(self.document)
  File "/usr/share/kabikaboo/src/file.py", line 97, in open
    return self.load_last_saved()
  File "/usr/share/kabikaboo/src/file.py", line 106, in load_last_saved
    return self.load_from_file_pickle(self.working_file)
  File "/usr/share/kabikaboo/src/file.py", line 288, in load_from_file_pickle
    return result, document
UnboundLocalError: local variable 'document' referenced before assignment
t0p@mars:~$ 

```

I've tried the ol' "turn it off and on again" solution: no good.  I've tried removing then reinstalling the program: still no good.  As a non-coder I have no idea what the above CLI error message means, other than that Kabikaboo was shut down "improperly" at some stage.  But to ride off into the sunset, never to return... a tad dramatic I think?

Anyone got any ideas?  I'm currently retrieving info by opening .kaboo files with gedit and manually copy-pasting relevant stuff to a new text file... but that's a lot of work, gotta be a way to revive kabikaboo, please???

Cheers!

---

### Post by t0p on 2013-05-22
BOUNCE Bounce Bounce bounce bounce bouncebouncebounce......

---

### Post by eec on 2013-05-30
[https://bugs.launchpad.net/ubuntu/+source/kabikaboo/+bug/623324](https://bugs.launchpad.net/ubuntu/+source/kabikaboo/+bug/623324)

It happens, i think, when you move the last opened document to somewhere else.

> Go into the ~/.kabikaboo folder and open settings.txt. In it, try changing AutoOpen = True to AutoOpen = False
If that doesn't work, temporarily rename the ~/.kabikaboo directory to something else to see if it will open.

---

### Post by boomi89 on 2014-02-20
thank you eec. After changing the setting AutoOpen = False, kabikaboo works correctly.  It solved this issue in my Ubuntu 12.04 LTS.

---

