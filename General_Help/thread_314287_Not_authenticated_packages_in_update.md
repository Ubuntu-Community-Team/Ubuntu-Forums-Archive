---
title: "Not authenticated packages in update"
date: 2006-12-07
forum: General Help
---

### Post by marianom on 2006-12-07
This morning when I started my edgy there were some update waiting to be installed.
Running synaptic, it tells me that several packages couldn't be authenticated.
These are:
```
x11-common
xserver-xorg-video-all
xserver-xorg-input-all
xutils
xbase-clients
xserver-xorg
gimp
gimp-data
libgtk2.0-dev
libgtk2.0-common
libgtk2.0-bin
libgtk2.0-0
libgimp2.0
gimp-python
libgnomevfs2-dev
libgnomevfs2-extra
libgnomevfs2-0
libgnomevfs2-common
gnome-games
gnome-games-data
gtk2-engines-pixbuf
libgnomeprintui2.2-dev
libgnomeprintui2.2-0
libgnomeprintui2.2-common
libgnomeprintui2.2-bin
vino
xorg
x-windows-system-core
gnome-system-tool

```

Do you guys installed them today? what's your advice regarding them? are they ok?

---

### Post by Delkster on 2006-12-07
Try refreshing your local package list, e.g. by hitting "Reload" in Synaptic, and see if the problem persists.

---

### Post by marianom on 2006-12-07
Yeap, the problem persists but now I get an error message:

```
W: GPG error: http://ar.archive.ubuntu.com edgy-updates Release: Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com edgy-updates Release: Las siguientes firms fueron inválidas: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

what could be translated as:

```
W: GPG error: http://ar.archive.ubuntu.com edgy-updates Release: The following signatures were invalidated: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://archive.ubuntu.com edgy-updates Release: The following signatures were invalidated: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

Since it says ***ar**.archive.ubuntu.com* I assume there's a problem in my country repositories. 
Maybe it's time to fill a bug.

---

