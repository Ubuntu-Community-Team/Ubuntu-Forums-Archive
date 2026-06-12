---
title: "Quick question"
date: 2008-01-07
forum: General Help
---

### Post by Geran on 2008-01-07
I'm trying to mount an nfs share and looking through the forums I see the term "UID" come up. Can someone explain what that is and how it needs to be fixed up to get my nfs working?

---

### Post by bodhi.zazen on 2008-01-07
To mount a nfs :

```
sudo mount ip:/share /mount/point
```

uid is sometimes an option to set ownership on a FAT or NTFS partition

UUID is a unique partition ID number.

Not sure either are related to NFS.

See this link : [http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

