---
title: "Problem solving procedures after package crash. (Deluge)"
date: 2008-01-03
forum: General Help
---

### Post by Bebbe on 2008-01-03
I am new to Linux but have been enjoying it for some time now. Yesterday Deluge crashed, however, and now it can't be started. I have restarted the computer...

I get the following in console:
```
no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
Capping download to -1 bytes per second
Capping upload to 97280 bytes per second
Traceback (most recent call last):
  File "/usr/bin/deluge", line 140, in <module>
    start_deluge()
  File "/usr/bin/deluge", line 127, in start_deluge
    interface = deluge.interface.DelugeGTK()
  File "/var/lib/python-support/python2.5/deluge/interface.py", line 53, in __init__
    '%s %s'%(common.PROGRAM_NAME, common.PROGRAM_VERSION), common.CONFIG_DIR)
  File "/var/lib/python-support/python2.5/deluge/core.py", line 258, in __init__
    self.state = pickle.load(pkl_file)
  File "/usr/lib/python2.5/pickle.py", line 1370, in load
    return Unpickler(file).load()
  File "/usr/lib/python2.5/pickle.py", line 858, in load
    dispatch[key](self)
  File "/usr/lib/python2.5/pickle.py", line 880, in load_eof
    raise EOFError
EOFError
``` 
I guess this is as good an occasion as any to learn problem solving procedures, So I hope someone can help me solve this problem. 

TIA..
B

---

### Post by Bebbe on 2008-01-03
I found this [http://ubuntuforums.org/showthread.php?t=638817]("http://ubuntuforums.org/showthread.php?t=638817")solution when I did a search for the entire error message ..sorry. 
I still don't understand how to figure out a solution on my own though...

---

