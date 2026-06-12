---
title: "Radio Tray stations."
date: 2014-03-30
forum: General Help
---

### Post by mn_voyageur on 2014-03-30
I recently learned about Radio Tray.

Is there a file that stores the addresses?  I have a small tablet at my office and would like to have the same "stations," without having to add them individually.

Thanks,
MarkN

---

### Post by mn_voyageur on 2014-03-30
I found what I needed!

/usr/share/radiotray/bookmarks.xml

MarkN

---

### Post by mn_voyageur on 2014-03-30
Okay, I edited the xml above.  However, the new bookmarks are not appearing in the list.

Any suggestions?

Thanks,
MarkN

---

### Post by ajgreeny on 2014-03-30
You need to copy the user's file in **/home/*user*/.local/share/radiotray/bookmarks.xml**, not the filesystem version which is probably the default that is included at installation.  Any stations you add are only in the version in your /home.

---

### Post by buzzingrobot on 2014-03-30
When Radiotray is running, right click on its icon in the panel and select "Preferences", then "Configure Radios".  There, you can add individual stations.  You don't need to edit the bookmark.xml file.

---

### Post by ajgreeny on 2014-04-01
This is what the OP was trying to avoid by copying the config file from one machine to another.  He was, I think, just copying the wrong file.

---

