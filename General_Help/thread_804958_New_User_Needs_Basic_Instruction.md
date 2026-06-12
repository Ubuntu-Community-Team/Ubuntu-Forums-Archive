---
title: "New User Needs Basic Instruction"
date: 2008-05-23
forum: General Help
---

### Post by General Specific on 2008-05-23
New/Returning to Linux.  Just installed Hardy 8.04.

Can someone recommend a beginners guide to the filesystem and program installation.

It's been a long time...

---

### Post by nick_h on 2008-05-23
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

---

### Post by ibuclaw on 2008-05-23
There is not really much to explain!

The filesystem is ext3. It is a journalising filesystem.

The main hierachy points are broken down as follows:
[PHP]
/           # Root Folder
/bin        # System Binaries Folder
/boot       # Kernel Folder
/etc        # Configurations Folder
/home       # Home Folder
/media      # Mounted Filesystems
/proc       # Loaded Hardware Modules
/var        # Stored App Data/Logs
/usr/bin    # Program Binaries Folder
/usr/local  # Local Apps Folder (Compiled from Source)
/usr/lib    # App/Library Folder
/usr/share  # App Folder/Shared Other (ie: icons, wallpapers)
[/PHP]

And you can install software in around 6 different ways:
[LIST]
[*]Synaptic   (System>Administration>Synaptic Package Manager)
[*]Add/Remove (Applications>Add/Remove...)
[*]apt-get    (Open Terminal, sudo apt-get [OPTION])
[*]aptitude   (Open Terminal, aptitude)
[*]dpkg       (Open Terminal, dpkg [OPTION])
[*]deb        (Download .deb file, double-click to install it)
[/LIST]

Regards
Iain

---

