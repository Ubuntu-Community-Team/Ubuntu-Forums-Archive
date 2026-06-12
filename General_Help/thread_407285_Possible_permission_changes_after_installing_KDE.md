---
title: "Possible permission changes after installing KDE"
date: 2007-04-12
forum: General Help
---

### Post by techgeek on 2007-04-12
First off I'm not a Linux guru, but I'm not a Linux newb either.  I have stumbled across a weird problem and I think it's associated with my installing the K desktop.  Everything I describe below seems to have occurred after it's installation.

First off when I use the File Browser, I can no longer navigate up to **THE** root directory, it only lets me get up to my /home directory.  Now I can work around this by going into View and selecting Show Hidden Files.  This didn't occur until I installed KDE.  Also when I first log in, my Windows File system icons and my USB HDD icon are placed on the desktop.  I can navigate through them and all is good.  At some point Windows File system icons disappear (the USB HDD remains) as a result of being unmounted (not sure what triggers this).  I can remount them from the terminal window and then of course they reappear on the desktop.  These same behaviors are seen in both Gnome/Nautilus and Gnome/KDE sessions.  I haven't investigated what triggers my Windows partitions unmounting, but I suspect it has something to do with switching from Nautilus to KDE.

Does anyone know what is causing this?

---

### Post by techgeek on 2007-04-12
I just confirmed the unmounting of my Windows Files System.  It occurs when I end a Gnome session and start a KDE session, then end the KDE session and return to the Gnome session.  The Windows partitions are still mounted when I get to the KDE session, but when I return to the Gnome session, it's dropped them.  Like I said before, it's just a matter of re-mounting them.  Now I understand why this only occurred after installing KDE, I didn't have a different session to switch back and forth from before installing it.  The other problem of losing the ability to browse root using File Browser (without telling it to show Hidden Files) is more annoying.  Is there anyway to reverse this without manually going and changing the properties of all the directories?

---

### Post by aysiu on 2007-04-12
Starting with Edgy Eft (6.10), Kubuntu started making the system folders hidden in an effort to make things "friendlier." It ended up just making people confused. The hidden folders are defined in the /etc/kubuntu-default-settings, I think.

More details here:
[https://bugs.launchpad.net/ubuntu/edgy/+source/kubuntu-default-settings/+bug/75017](https://bugs.launchpad.net/ubuntu/edgy/+source/kubuntu-default-settings/+bug/75017)

---

