---
title: "Thunderbird profile"
date: 2008-06-05
forum: General Help
---

### Post by DeVonne on 2008-06-05
Hello, I have thunderbird and am trying to get it to read the profile from windows, well the 2 methods I tried did not work

the profile.ini method setting the path to the one on windows

[General]
StartWithLastProfile=0

[Profile0]
Name=default
IsRelative=0
Path=/media/hdb1/Craig/ThunderbirdPortable/Data/profile


and making a ls -s link to the folder on windows like this

ln -s /media/hdb1/Craig/ThunderbirdPortable/Data/profile /home/visionary/.mozilla-thunderbird/i8o2p4p1.default

Both methods make it say it is already open..

---

### Post by Nepherte on 2008-06-05
The last method should certainly work. You'll probably still have to switch to the profile you symlinked:
```
thunderbird -profilemanager
```
There you can choose what profile you want. If that doesn't work you might want to create a new profile and change the folder of the profile to a disk your windows installation can access.

---

