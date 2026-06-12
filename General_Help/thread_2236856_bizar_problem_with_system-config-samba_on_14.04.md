---
title: "bizar problem with system-config-samba on 14.04"
date: 2014-07-29
forum: General Help
---

### Post by mdurham on 2014-07-29
Hi,
here is the result of trying to run from a terminal, obviously it doesn't run! 

mike@downstairsPA1:~$ gksu system-config-samba
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 82, in __init__
    self.samba_data = sambaParser.SambaParser(self)
  File "/usr/share/system-config-samba/sambaParser.py", line 185, in __init__
    self.parseFile ()
  File "/usr/share/system-config-samba/sambaParser.py", line 225, in parseFile
    token = self.createToken (line, section) 
  File "/usr/share/system-config-samba/sambaParser.py", line 310, in createToken
    name, value = line.split ("=", 1)
ValueError: need more than 1 value to unpack

I have re-installed it a couple of times with the same result.
Any help with what's going on here would be appreciated.

Cheers, Mike

---

