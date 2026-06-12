---
title: "Dropbox daemon install stuck"
date: 2014-02-03
forum: General Help
---

### Post by Veerdavid on 2014-02-03
Hi Everyone,

I have been using dropbox for a long time on Ubuntu 12.04, but one day it got stuck syncing so I killed it with pkill (as it stopped responding). Unfortunately I didn't check afterwards if it worked, so I dont know if this has anything to do with my problem.
When I wanted to use dropbox again (right after startup) I noticed that dropbox wasn't running. Starting it from dash did nothing, so I tried starting from terminal, but that told me that the daemon wasn't installed. I tried installing it with 'dropbox start -i', as suggested. This started downloading and then unpacking, but the unpacking got stuck at 90 some percent. After this I reinstalled dropbox, but the problem remained the same...
Does anyone know what could the cause be or how to fix it?

Thanks,
Dávid

---

### Post by Erik1984 on 2014-02-03
If all else fails you could delete the (hidden) folders .dropbox and .dropbox-dist from your home directory and try to install dropbox again so it will start with fresh settings files. You can leave the Dropbox folder with all your files in place, the installer will notice it exists.

---

### Post by Veerdavid on 2014-02-05
I did that and it solved the installation problem, but now I don't have the little dropbox icon on the menu bar. (Or whatever it is called, where the clock is.)

---

### Post by acornbrain on 2014-03-01
I am having a similar issue. (12.04) For a week or so now, every time I turn on my laptop, I am prompted to install dropbox. I click OK, it does it's thing, but never quite seems to 'stick'. My Dropbox folder is still there in Nautilus, but no indicator icon in the top panel.

---

### Post by bapoumba on 2014-03-01
May be try to unlink the computer from the dropbox website and link it again : [http://ubuntuforums.org/showthread.php?t=2181303&p=12874649#post12874649](http://ubuntuforums.org/showthread.php?t=2181303&p=12874649#post12874649)
Other posts from this thread may help you too.

---

### Post by rjt69 on 2014-03-01
Is it possible the hard drive is full?  Look at the ~/.dropbox/ or whatever folder is used for cache.

---

### Post by acornbrain on 2014-03-02
Euroman's solution worked for me (reply #2)... deleted the two .hidden folders and re-installed dropbox. Before I did that, I unlinked my laptop via the Dropbox site per Bapoumba's suggestion (reply #5). Not sure if that step was unecessary or not, but that's what I did.

All seems to be working normally again. Thank you for the help.
-ab

---

### Post by bapoumba on 2014-03-02
Glad to see you got it to work, please consider marking your thread as solved : [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
Cheers :)

---

