---
title: "Window display problem (Gutsy)"
date: 2007-10-22
forum: General Help
---

### Post by audunmb on 2007-10-22
This is bad. My windows go all dark, not all windows luckily, but some. Mostly with Evince (PDF-viewer), but it did happen with other windows inluding emacs and firefox. Take a look at the attached screenshot.
The application is responding (right-click gives a context menu), it is simply that I cannot view what's in them as they're all dark. 

It mostly happens when I have more than one window from the same application open at the same time. 

This is on a newly upgraded Gutsy Gibbon, with compiz running. 

Any ideas?

---

### Post by audunmb on 2007-10-23
Other threads for the same problem:

- [http://ubuntuforums.org/showthread.php?t=587927](http://ubuntuforums.org/showthread.php?t=587927)
- [http://ubuntuforums.org/showthread.php?t=586987](http://ubuntuforums.org/showthread.php?t=586987)

Seems like it's driver problem with nvidia... and the only option is to disable compiz...

---

### Post by audunmb on 2007-11-01
Fixed it by installing nvidia-glx-new it seems

---

