---
title: "Chrome Won't Launch"
date: 2013-11-16
forum: General Help
---

### Post by mfucci on 2013-11-16
Hello,

After doing an update to the newest version of Chrome on a friend's computer, it will no longer launch. If launched from the terminal, I get the following error:

chrome nacl helper process running without a sandbox

Most likely you need to configure your SUID sandbox correctly

I've tried removing and reinstalling a number of times with no success. I think this may be a permissions issue but am not familiar with how to resolve it. Any help would be most appreciated. Thanks!

Edit: Computer is running 12.04

---

### Post by mfucci on 2013-11-17
Seems like I'm not the only one:

[http://productforums.google.com/forum/#!topic/chrome/5EmprHC36WU](http://productforums.google.com/forum/#!topic/chrome/5EmprHC36WU)

---

### Post by Frogs Hair on 2013-11-17
Open the home folder press Ctr+H . This will display hidden folders and in the .config folder you will find the Google Chrome folder . Delete the the folder and re-install.
Note: If don't use sign in to Chrome to sync your bookmarks and extensions export your bookmarks before deleting the folder. I was unaffected by the update ?

---

### Post by mfucci on 2013-11-17
> **Frogs Hair said:**
> Open the home folder press Ctr+H . This will display hidden folders and in the .config folder you will find the Google Chrome folder . Delete the the folder and re-install.
Note: If don't use sign in to Chrome to sync your bookmarks and extensions export your bookmarks before deleting the folder. I was unaffected by the update ?

Thanks. I gave that a try yesterday but the result was the same.

---

### Post by mfucci on 2013-11-18
Any other ideas?

---

### Post by mfucci on 2013-11-18
Managed to get the previous version of Chrome and installed that. Works fine. This seems to be an issue with the packaging of the newest version of Chrome. I suspect it may only affect a specific processor type (not sure which, but my friend's is an older AMD).

---

### Post by majk2 on 2014-06-27
OK I had this issue this morning after updating Ubuntu with System Updater. My Chrome would not open from Launcher. 

I eventually solved this issue as follows:
[http://digwork.com/index.php/resources/17-ubuntu-how-to-fix-app-that-won-t-start-from-launcher](http://digwork.com/index.php/resources/17-ubuntu-how-to-fix-app-that-won-t-start-from-launcher)

---

