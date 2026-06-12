---
title: "Scripting"
date: 2020-05-11
forum: General Help
---

### Post by Quarkrad on 2020-05-11
I have written a simple script that backs up my personal data and then powers down the pc. To run the script I have added a custom application launcher to my top panel (ubuntu mate 20.04).  Everything works well, data is backed up and the pc powers down.  Is it possible to have a terminal launch showing the progress of the backup on the Desktop?  At the moment I click on the (custom launcher) icon and, obviously, nothing happens until the pc powers down. It would be nice if I could see what was happening.

---

### Post by kostkon on 2020-05-11
Just add the line
```
Terminal=true
```
in your .desktop file.

---

### Post by Quarkrad on 2020-05-11
That did it - thank you.

---

