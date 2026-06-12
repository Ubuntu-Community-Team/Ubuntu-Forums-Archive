---
title: "How to open bookmarks in same Konqueror window"
date: 2007-12-22
forum: General Help
---

### Post by johnbuck on 2007-12-22
Konqueror is capable of tabs browsing, however select bookmark from the Kmenu will open a new Konqueror window. The solution as below

edit the file /usr/share/applications/kde/kfmclient_dir.desktop 

change the line Exec=kfmclient openURL %u inode/directory
to Exec=kfmclient newTab %u inode/directory

---

