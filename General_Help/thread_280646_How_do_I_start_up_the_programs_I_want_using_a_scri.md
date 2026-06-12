---
title: "How do I start up the programs I want using a script?"
date: 2006-10-19
forum: General Help
---

### Post by Count Noobulus on 2006-10-19
Would like to set Ubuntu to auto-run firefox after it loads using a script. What do I have to type in a file and where do I put it?

---

### Post by kerry_s on 2006-10-19
Just put it in your home directory. You can make it hidden by putting a " . " in the front of the name like this " .start ". In the file put->

#!/bin/sh

firefox &

The important thing is to make it executable, then just add the path to gnome session startup. Also if you want to start the minimized to the system tray. You can use alltray, i use kdocker because i'm running kde.

---

