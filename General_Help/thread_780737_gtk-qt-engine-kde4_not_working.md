---
title: "gtk-qt-engine-kde4 not working"
date: 2008-05-03
forum: General Help
---

### Post by a2h on 2008-05-03
I have Kubuntu 8.04 KDE4, and have installed gtk-qt-engine-kde4, yet Synaptic still uses the ugly GTK theme.

I have went into the configuration and changed the appearance to copy from the current KDE4 theme, and have restarted a few times (being told that KDE needs a restart to have the config applied), to no avail.

I have version 1.1-0ubuntu1 of the package.

---

### Post by Justin Trouble on 2008-05-28
I've only just installed gtk-qt-engine-kde4 and I can confirm that Synaptic still looks ugly. Having said that it's worked a treat with Firefox 3 and Thunderbird.

---

### Post by liquidcable on 2008-08-10
Synaptic still looks bad because it is starting up with root privileges (you must enter your sudo password when it starts up).  The gtk-qt-engine-kde4 theme only works for the current user not other users (ie. root).

The old school way of solving this was to log into KDE with the root user, and activate the gtk-qt-engine-kde4 theme for GTK apps...but Ubuntu does not what you to login as root.  There must be a better way but I don't know it right now.

---

### Post by blacx on 2008-11-29
Try installing the package libbonoboui2-0

---

### Post by Nonexistent on 2009-01-05
Workaround: 
```

sudo mv ~/.gtkrc-2.0-kde4 /root/.gtkrc-2.0

```
from [https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine-kde4/+bug/225076/comments/5](https://bugs.launchpad.net/ubuntu/+source/gtk-qt-engine-kde4/+bug/225076/comments/5)

---

