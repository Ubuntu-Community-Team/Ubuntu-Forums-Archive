---
title: "Kabikaboo not working anymore...."
date: 2013-02-10
forum: General Help
---

### Post by t0p on 2013-02-10
I've been using Kabikaboo for a while, and it's very useful.  But now it won't work.  I've googled and rebooted and the rest of it, but nothing.

If I try to start it by clicking on the Kabikaboo, nothing happens.  No error message, nothing at all.  If I try to start it via terminal this is what I get:

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

I see an "improper shutdown" referenced, and I think this coincided with a kernel update (not sure about that last bit).

I can recover my data manually, by copying and pasting text into gedit, but that's a real pain.

Anyone help?  I'm using Ubuntu 12.04 64-bit.

Cheers!

---

