---
title: "mysterious script"
date: 2012-12-09
forum: General Help
---

### Post by staticVoid89 on 2012-12-09
Hello all!

I am experiencing a little difficultly trying to prevent a script from being executed at boot. The script in question is one I created a while back and despite numerous attempts, I cannot seem to prevent the script from being executed.

The problem is I created the script a while back and cant remember how I implemented it to be executed. Which ultimately makes the problem quite tedious, however I've checked some of the most common areas in which I could have had it executed but despite removing what I can this still takes no effect.

firstly I removed the entry from the gui start-up application panel. in addition i have also checked my update-rc.d, .bashrc, along with all my cron jobs but still had no success. I have even deleted the original script that was being executed but still I have the same behaviour?

Any suggestions towards how I might have had the script called, or an effective way to prevent it would be much appreciated.

Kind regards.

---

### Post by Frogs Hair on 2012-12-09
Possibly related.

[http://www.unix.com/shell-programming-scripting/203477-remove-script-still-running-background.html](http://www.unix.com/shell-programming-scripting/203477-remove-script-still-running-background.html)

[http://superuser.com/questions/282054/extract-executable-script-from-memory-in-ubuntu-linux](http://superuser.com/questions/282054/extract-executable-script-from-memory-in-ubuntu-linux)

---

### Post by Habitual on 2012-12-09
Did you check /etc/rc.local?

---

