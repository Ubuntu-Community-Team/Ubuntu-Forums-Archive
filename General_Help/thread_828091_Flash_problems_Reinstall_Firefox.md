---
title: "Flash problems/ Reinstall Firefox?"
date: 2008-06-13
forum: General Help
---

### Post by earthbound01 on 2008-06-13
So I'm something of a n00b.  I started out wanting to use a flash-based website, isketch.net, and I couldn't get it to work.  I tried reinstalling adobe shockwave.  I then tried many things, and now my browser is somewhat buggy.  
What's the most expedient way to undo everything and start fresh?  
A clean install of 8.04?

---

### Post by NilsE on 2008-06-13
Go into Synapric package manager and uninstall whatever you have for flash and either install or reinstall flashplugin-nonfree

---

### Post by wolfen69 on 2008-06-13
completely remove firefox and flash. then ```
sudo apt-get clean
``` then go to home folder and do ctrl-H to show hidden files. delete the .mozilla folder. empty trash. then re-install firefox and flashplugin.

---

### Post by joshsmith on 2008-06-13
you are probably seeing the same problem as this:
[http://ubuntuforums.org/showthread.php?t=827955](http://ubuntuforums.org/showthread.php?t=827955)

---

