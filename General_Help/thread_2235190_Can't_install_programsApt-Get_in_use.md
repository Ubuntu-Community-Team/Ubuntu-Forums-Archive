---
title: "Can't install programs/Apt-Get in use"
date: 2014-07-19
forum: General Help
---

### Post by caneely2000 on 2014-07-19
Hey new Linux user here. Sorry if this question has been asked before but I was installing Dropbox through terminal and the install crashed. Now whenever I try to install through terminal it gives me the message :

"E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?"

Similarly when I try to use Software Center it tells me "Waiting for apt-get to exit". 

Someone help me figure this out please...

---

### Post by Impavidus on 2014-07-19
To prevent multiple package managers from running at the same time, the package manager creates a lock. Because of the crash, the package managers failed to remove the lock. So now every package manager thinks another package manager is already running.

Doublecheck that no other package managers are running (rebooting does the trick) and try removing the lock manually:```
sudo rm /var/lib/dpkg/lock
```

---

