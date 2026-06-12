---
title: "Deluge won't start"
date: 2008-05-11
forum: General Help
---

### Post by kzlazy on 2008-05-11
So,

I am using an old Hp omnibook xe 4500 laptop with Gutsy Gibbon and among other stuff I installed and used deluge bit torrent client.

Last time I tried to run it, it did not respond and after several times, I tried to open it from a console and got the following message

:~$ deluge
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to 614400 bytes per second
Capping upload to 30720 bytes per second
Raising error: 
Error: ''
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 53, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 263, in __init__
    self.sync(True)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 837, in sync
    raise e
deluge.core.FilesystemError: ''



I tried to unistall and re-install deluge by synaptic but nothng changed. Anyone might have an idea on that? Any help will be appreciated.

Thanx.


PS I appear as hardy user because the above laptop is my minor pc.

---

### Post by kzlazy on 2008-05-11
anybody?

---

### Post by mixtri on 2008-06-01
I have the same problem as well. 
Anybody? please?

---

