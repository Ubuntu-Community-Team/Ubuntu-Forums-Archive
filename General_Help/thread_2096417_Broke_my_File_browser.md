---
title: "Broke my File browser?"
date: 2012-12-19
forum: General Help
---

### Post by alphaamanitin on 2012-12-19
So, not sure what I did.  I tried to share a folder with my virtual box, via the mount -t command, didn't work and now when I open xubuntu's File Browser and try to open my user folder I get this message: > Failed to open directory "user". Error when getting information for file '/home/user/.gvfs': Transparent endpoint is not connected."I can still navigate to it via command line and the computer boots fine and the like, so what did I do?  

AlphaA

***Update***

Found answer on google.  I kept typing in transparent in place of transport so google was having issues.  Anyway, just needed to unmount:```
fusermount -u ~/.gvfs 
```.

AlphaA

---

