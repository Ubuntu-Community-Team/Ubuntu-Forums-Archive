---
title: "wine-doors problems"
date: 2008-01-27
forum: General Help
---

### Post by caricc on 2008-01-27
I made some changes to wine-doors configuration to read the wine registry but not anything else. Now when I try to start wine-doors I get nothing. So I tried to use the command line adn this is what I get:

Started logging session
Traceback (most recent call last):
  File "/usr/bin/wine-doors", line 22, in <module>
    from queue import queue
  File "/usr/share/wine-doors/src/queue.py", line 6, in <module>
    from application import ApplicationPack
  File "/usr/share/wine-doors/src/application.py", line 7, in <module>
    from packlist import packlist
  File "/usr/share/wine-doors/src/packlist.py", line 634, in <module>
    packlist = PackList()  
  File "/usr/share/wine-doors/src/packlist.py", line 167, in __init__
    self.GetInstalledPacks()
  File "/usr/share/wine-doors/src/packlist.py", line 183, in GetInstalledPacks
    for installed in wine.installedFromReg():
  File "/usr/share/wine-doors/src/wine.py", line 379, in installedFromReg
    if self.getRegistry( approot + app, "FriendlyName" ) != "":
  File "/usr/share/wine-doors/src/wine.py", line 300, in getRegistry
    [thiskey, thisval] = line.split( "=")
ValueError: too many values to unpack

Any help would be appreciated. 
Thanks in advance.

---

### Post by MoLE on 2008-02-03
I'd suggest posting on the wine-doors mailing list or filing a bug.  I'm not sure if there's an IRC channel as well, but might be worth checking.

---

