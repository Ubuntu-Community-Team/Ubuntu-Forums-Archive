---
title: "Notes won't open..."
date: 2015-04-16
forum: General Help
---

### Post by stretch4 on 2015-04-16
I'm using Xubuntu 14.10

When I try to open notes from the application menu nothing happens.
When I try to start it from the console, it just goes back to the command prompt.
```
$$ xfce4-notes
$$
```
I tried reinstalling it. Which seemed to go fine...
```
$$ sudo aptitude reinstall xfce4-notes
[sudo] password for stretch: 
The following packages will be REINSTALLED:
  xfce4-notes 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 105 kB of archives. After unpacking 0 B will be used.
Get: 1 http://us.archive.ubuntu.com/ubuntu/ utopic/universe xfce4-notes amd64 1.7.7-3ubuntu2 [105 kB]
Fetched 105 kB in 0s (144 kB/s) 
(Reading database ... 198097 files and directories currently installed.)
Preparing to unpack .../xfce4-notes_1.7.7-3ubuntu2_amd64.deb ...
Unpacking xfce4-notes (1.7.7-3ubuntu2) over (1.7.7-3ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
                                         
$$
```

But it still won't start. Any ideas?

---

### Post by dino99 on 2015-04-16
i have no clue with xfce's app, but reinstalling is not enough to get rid of corrupt installation; purge that app first , then install it back: otherwise report a bug.

---

### Post by stretch4 on 2015-04-16
I purged and installed. Still won't start. Now when I try to start it, nothing happens for a few seconds, and then it gives me a warning message and back to the command prompt.
```

$$ sudo aptitude purge xfce4-notes
[sudo] password for stretch: 
The following packages will be REMOVED:  
  xfce4-notes{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 738 kB will be freed.
Do you want to continue? [Y/n/?] y
(Reading database ... 198087 files and directories currently installed.)
Removing xfce4-notes (1.7.7-3ubuntu2) ...
Purging configuration files for xfce4-notes (1.7.7-3ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
                                         
$$ sudo aptitude install xfce4-notes -y
The following NEW packages will be installed:
  xfce4-notes 
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/105 kB of archives. After unpacking 738 kB will be used.
Selecting previously unselected package xfce4-notes.
(Reading database ... 198015 files and directories currently installed.)
Preparing to unpack .../xfce4-notes_1.7.7-3ubuntu2_amd64.deb ...
Unpacking xfce4-notes (1.7.7-3ubuntu2) ...
Processing triggers for mime-support (3.55ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu2) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
                                         
$$ xfce4-notes

** (xfce4-notes:15676): WARNING **: main-status-icon.vala:37: Status Icon is not embedded
$$ 

```

---

### Post by ajgreeny on 2015-04-16
It may be the configuration in your home so try deleting the files for notes (or just rename then for now) and try again.

~/.config/xfce4/xfce4-notes.gtkrc
~/.config/xfce4/xfce4-notes.rc
~/.config/xfce4/panel/xfce4-notes-plugin-41.rc

Incidentally are you sure notes is not starting?  In my 14.04 notes always start minimised as an icon in the tray which I click to view a note.

---

### Post by stretch4 on 2015-04-16
> **ajgreeny said:**
> Incidentally are you sure notes is not starting?  In my 14.04 notes always start minimised as an icon in the tray which I click to view a note.

Hey, whaddaya know? It was starting. I just didn't have "Notification Area" on my panel. Once I added it to my panel, the notes icon appeared. I wouldn't have expected it to launch minimized. Thanks!

---

