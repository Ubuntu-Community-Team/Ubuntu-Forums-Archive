---
title: "KlamAV context menu not working"
date: 2006-12-11
forum: General Help
---

### Post by kracheck on 2006-12-11
I installed KlamAV. When I right-click on a file and choose "Actions-Scan with KlamAV..." nothing actually happens. Anyone can tell me how I can get this context menu working ? Thanks in advance

---

### Post by kracheck on 2006-12-14
Got this answer on the newsgroup
[http://sourceforge.net/mailarchive/forum.php?forum_id=42209](http://sourceforge.net/mailarchive/forum.php?forum_id=42209)

"Look for klamav-dropdown.desktop on your filesystem and modify it to use the appropriate script - it may be referring to ScanWithKlamAV.sh. "

Removing the "sh" in front of "sh ScanWithKlamAV" in the file klamav-dropdown.desktop located in /usr/share/apps/konqueror/servicemenus/klamav-dropdown does the trick.  Running Kubuntu 6.10 with KlamAV 0.37.

---

