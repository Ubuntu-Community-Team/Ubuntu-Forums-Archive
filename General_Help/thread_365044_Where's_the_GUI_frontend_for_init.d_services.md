---
title: "Where's the GUI frontend for init.d services?"
date: 2007-02-19
forum: General Help
---

### Post by CaptSaltyJack on 2007-02-19
Sorry, bad title.. I meant /etc/rc.d

Kubuntu had this nice frontend (a stoplight icon) that shows you all services running.. mysql, apache, ssh, and let you start/stop them and set that behavior in the /etc/rc* dirs.  I don't see this in Ubuntu.. does it exist?

---

### Post by yabbadabbadont on 2007-02-19
rcconf, bum, sysv-rc-conf all provide a frontend for manipulating the /etc/rc?.d symlinks.  Only bum is graphical, the other two provide ncurses frontends (textmode dialogs).  If you knew what that package was called from kubuntu, you could install it and use it in gnome.  KDE programs will work in Gnome.

---

### Post by CaptSaltyJack on 2007-02-19
> **yabbadabbadont said:**
> rcconf, bum, sysv-rc-conf all provide a frontend for manipulating the /etc/rc?.d symlinks.  Only bum is graphical, the other two provide ncurses frontends (textmode dialogs).  If you knew what that package was called from kubuntu, you could install it and use it in gnome.  KDE programs will work in Gnome.

Great, thanks!  I'll check out Ubuntu's bum later.. :lolflag:

---

### Post by yabbadabbadont on 2007-02-19
> **CaptSaltyJack said:**
> Great, thanks!  I'll check out Ubuntu's bum later.. :lolflag:

Yeah, I love that name too.  :lol:

---

### Post by CaptSaltyJack on 2007-02-19
Yuck.. not liking it.  Kubuntu's runlevel manager is leagues better.

bum has no way of adding your own custom items.. for example, I installed ssh, and it's running, but it's not in /etc/rc* anywhere so I believe it won't run on startup, and bum doesn't list it.  Whereas on Kubuntu, ssh is listed right away in the runlevel manager.

Also, I installed mysql which now shows up in bum, but it doesn't know if it's running or not (a question mark shows instead of a light bulb).  And if I try to stop/start it, it says it worked but it really doesn't do anything.

Really bad.  Someone ought to work on a nicer runlevel config for Ubuntu.  Kubuntu's is perfect.

---

### Post by yabbadabbadont on 2007-02-19
> **CaptSaltyJack said:**
> Yuck.. not liking it.  Kubuntu's runlevel manager is leagues better.

bum has no way of adding your own custom items.. for example, I installed ssh, and it's running, but it's not in /etc/rc* anywhere so I believe it won't run on startup, and bum doesn't list it.  Whereas on Kubuntu, ssh is listed right away in the runlevel manager.

Also, I installed mysql which now shows up in bum, but it doesn't know if it's running or not (a question mark shows instead of a light bulb).  And if I try to stop/start it, it says it worked but it really doesn't do anything.

Really bad.  Someone ought to work on a nicer runlevel config for Ubuntu.  Kubuntu's is perfect.

You need to read through the BUM thread.  The behavior you are seeing is a known bug.  It actually *does* make the changes, it's just that they don't show up until you exit and re-enter the program....  (You'll probably see a post by me confirming that problem to the developer :))

---

### Post by CaptSaltyJack on 2007-02-19
sysv-rc-conf will do the trick..very nice.  Not pretty, but it works, and it shows EVERYTHING.  rcconf and bum are missing tons of services (like ssh).  sysv-rc-conf doesn't miss a thing.

Thanks!

---

