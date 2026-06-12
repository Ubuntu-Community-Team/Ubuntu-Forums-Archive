---
title: "Restarting crashed application."
date: 2008-04-27
forum: General Help
---

### Post by ldt0 on 2008-04-27
I'm running a mediacenter with xbmc on Ubuntu. I have xbmc set to the default windowmanager, i have simply created a ~/.xsession file that launches xbmc. It currently contains only this:

#!/bin/sh
~/xbmc/xbmc

The problem however is that xbmc sometimes crashes (Not often though, but once or twice a week or so, it's still in alpha you know), throwing me out to the login screen. How do i get it to simply restart xbmc instead? It's probably an easy fix, but my linux scripting skills are zero so i'd appreciate any help. :)

---

### Post by ryanhaigh on 2008-04-27
You could make a simple shell script to check whether or not xbmc is running and if it is not found in the process table restart it.

This should be all you need:
[http://www.linuxquestions.org/questions/linux-software-2/shell-script-to-start-another-program-if-not-running.-625589/](http://www.linuxquestions.org/questions/linux-software-2/shell-script-to-start-another-program-if-not-running.-625589/)

---

