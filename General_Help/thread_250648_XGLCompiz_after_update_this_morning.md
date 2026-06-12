---
title: "XGL/Compiz after update this morning"
date: 2006-09-04
forum: General Help
---

### Post by jr.gotti on 2006-09-04
[http://www.compiz.net/topic-3881-compiz-broke-this-morning-after-update](http://www.compiz.net/topic-3881-compiz-broke-this-morning-after-update)

Instead of using "compiz-start.py" as your startup use "compiz-start"

Make sure CSM is installed.

Then run "csm" in the terminal to change any of the settings for Compiz/

If changes in csm don't have any effect, then go into the terminal and type "sudo chmod 755 ~/.compiz -R"
if it complains about a folder being missing, then create a ".compiz" folder in ur home folder and run the command again.

Not taking credit for this...click the link at the top...I just cleaned it up a bit.

---

### Post by Zarathu on 2006-09-04
Great!  That helped my settings a bunch, thanks!

---

