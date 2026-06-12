---
title: "Software Updater &amp; Package Upgrade"
date: 2016-06-02
forum: General Help
---

### Post by cessanfrancisco on 2016-06-02
I am running Ubuntu 16.04, and when I run:

```
sudo apt update
```

I get a message telling me there are packages that are available for upgrade but I need to run:

```
apt list --upgradable
```

...which I then proceed to do.  This gives me a list of packages available for upgrade.

So, then, I run the Software Updater app and it does its thing.  Then I run, again:

```
apt list --upgradable
```

...and it appears that Software Updater did not upgrade all packages.  Then I have to run (in order to upgrade the remaining packages):

```
sudo apt upgrade
```

Can anyone explain why Software Updater won't upgrade all the packages?

Thanks in advance

---

### Post by deadflowr on 2016-06-02
from memory, the software updater/update manager has a built in function called Phased Updates, that make it so updates are phased out slowly to users, a small selection at a time.
apt does not have this feature, so any new update will instantly show in the apt commands.

---

### Post by Dennis N on 2016-06-02
> Can anyone explain why Software Updater won't upgrade all the packages?

This is probably due to the "phased updates" system used by Software Updater, in effect since 2013. The system is explained here:

[https://lwn.net/Articles/563966/](https://lwn.net/Articles/563966/)

The article refers to "Update Manager" which was the former name for the GUI updater.

---

### Post by Tony_Bennett on 2016-06-02
This may be the case, but it can cause some confusion.
Upon logging in I have seen a "Notification" that there are updates
that need to be applied.  Yet, when I go to "Software Updater", it tells
me the software is up to date.  I then open "Ubuntu Software" (gnome-software),
and it has the "update" tab with a colored "number" on it, indicating there are updates
available... I can use it to apply those updates... or I can use "sudo apt update", 
and get a list of packages that can be updated... which are successfully updated
by "sudo apt upgrade".

My point is there seems to be a dis-joint between a log-in notification, "software updater",
"Ubuntu Software" and "apt update"....

I did not see this behaviour in 12.04 or in 14.04.

---

### Post by Bucky Ball on 2016-06-03
```
sudo apt update
sudo apt full-upgrade
```

... is all you need.

The Software Updater in 16.04 appears to have a few glitches from time to time at this early stage. Appears Software Centre/Gnome Software has had some teething issues too.

I use Synaptics and update/upgrade via the terminal, so ...

---

