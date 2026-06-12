---
title: "cron diff from xterm"
date: 2007-09-21
forum: General Help
---

### Post by munruh on 2007-09-21
What is the different between cron firing up a bash script and xterm firing up the script?
I have a working script when executed from xterm, but it will not work when called from cron.
I know for a fact that cron is working.

This is getting frustrating!  :confused:

---

### Post by McNils on 2007-09-21
Scripts runned from cron have a very limeted environment. Check the PATH environment variable.

---

