---
title: "Pidgin MusicTracker issue"
date: 2008-07-07
forum: General Help
---

### Post by s_esquibel on 2008-07-07
About 10 seconds into startup of pidgin, it freezes. I have run a pidgin -d and have disabled plugins one by one until I found the culprit, musictracker.

Below are the errors that are found through "pidgin -d".

Any thoughts on where I can find these libraries? I have tried multiple ways. apt-get, synaptic, etc.

I am using pidgin 2.4.1 and Ubuntu 8.04

Thanks in advance!

```
(15:20:05) core-musictracker: libxmms.so 
(15:20:05) core-musictracker: Failed to load library libxmms.so
(15:20:05) core-musictracker: xmmsctrl not initialized properly
(15:20:05) core-musictracker: libxmms.so.1 
(15:20:05) core-musictracker: Failed to load library libxmms.so.1
(15:20:05) core-musictracker: xmmsctrl not initialized properly
(15:20:05) core-musictracker: libaudacious.so 
(15:20:05) core-musictracker: Failed to load library libaudacious.so
(15:20:05) core-musictracker: xmmsctrl not initialized properly
(15:20:05) core-musictracker: libaudacious.so.3 
(15:20:05) core-musictracker: Failed to load library libaudacious.so.3
(15:20:05) core-musictracker: xmmsctrl not initialized properly
```

---

### Post by Sarmacid on 2008-10-02
Had the same issue while using Amarok. Go to [http://ubuntuforums.org/showthread.php?p=5897264#post5897264](http://ubuntuforums.org/showthread.php?p=5897264#post5897264)

---

