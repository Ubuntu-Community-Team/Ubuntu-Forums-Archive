---
title: "Error when trying to use synaptic?"
date: 2017-01-15
forum: General Help
---

### Post by lukemone on 2017-01-15
I am a novice ubuntu user, and I use synaptic to uninstall applications. For some reason when I open synaptic, I get this error.

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) is already running.
Please close that application first.

The thing is nothing else is open. What do I do?

---

### Post by oldos2er on 2017-01-15
Run ```
ps aux | grep apt
``` to see if another package manager program is running. If not, you may need to manually remove the lock file.

More info here: [http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process](http://askubuntu.com/questions/15433/unable-to-lock-the-administration-directory-var-lib-dpkg-is-another-process)

---

### Post by ajgreeny on 2017-01-15
It can also happen if your system is set to auto-upgrade security packages in the background with no action on your part; that may be active at the same time as you want to carry out some package management activity, so you may find it will work fine in a short while one the auto-upgrade is finished.

That's one of the reasons I disable that auto-upgrade system on my machine; I like to keep full control.
You can disable it if you wish, in the upgrades tab of Software-sources, but I believe it is the default to allow it to happen in the background, so make your choice, but whatever you do, it is wise to make sure your OS is kept fully updated.

---

