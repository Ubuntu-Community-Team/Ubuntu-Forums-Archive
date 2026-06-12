---
title: "what is nautilis and how do use it?"
date: 2014-03-14
forum: General Help
---

### Post by drew14 on 2014-03-14
new to ubuntu. Im hoping to find out where my programs are filed under. (new from win xp,sorry...lol)

---

### Post by 3rdalbum on 2014-03-14
To find your programs:

Click on the Ubuntu button on the top left corner of the screen. Click on the second icon along the bottom of the Dash that opens up - depending on the version of Ubuntu it will either look like a ruler and two pens, or an "A". Under 'installed' click "See x more results" to show them all, or click the Filter Results button on the right-hand side to filter by category.

What is Nautilus:

Nautilus is the name of the file browser on Ubuntu. When you double-click on a folder and its contents open up in a new window, that's Nautilus.

---

### Post by buzzingrobot on 2014-03-14
Directories in Linux are organized hierarchically, starting with a directory simply named '/'.  Think of the overall directory structure as a bit like an upside-down tree, with all directories except '/' being "inside" another directory, and everything "inside" '/'.

A directory called '/home' exists.  Inside it, directories are created with names that correspond to each user's login name.   That is, someone whose username is 'Bob' will see that a '/home/bob' directory exists.  Bob has complete access to his home directory and can do with it whatever he wants.  It's also where the configuration files that are specific to Bob are created and located. (E.g., the browser Bob uses will keep the configuration files it reads when Bob runs it in /home/bob.

The executable parts of applications are located in other portions of the directory hierarchy. Windows might call them 'system' directories, but that expression is not traditionally used in Linux.


Here's a short post that might be informative: [https://help.ubuntu.com/community/LinuxFilesystemTreeOverview](https://help.ubuntu.com/community/LinuxFilesystemTreeOverview).

---

### Post by oldos2er on 2014-03-14
> **drew14 said:**
> new to ubuntu. Im hoping to find out where my programs are filed under. (new from win xp,sorry...lol)

Nautilus is Gnome's file manager. If you're looking for executables see /usr/bin/, /bin/, and /sbin/. The [Linux file system hierarchy]("https://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") is quite a bit different than Windows.

---

### Post by Tristan_Williams on 2014-03-14
I think I may be able to help a little too. 

In Windows, you are familiar with the C:\ Drive. Well, in Linux, C:\ is replaced by / or the "root" filesystem.

Also, Windows has folders named Program files, Users, and a bunch of other crap that no one knows where anything could be located.

In linux, you know where everything is located.

/ is the entire filesystem. Everything is inside of /

/home is where all of the user profiles are located.

Base system software is located in /bin
other software is located in /usr/bin, /usr/sbin, and /sbin 

Most system settings are located within /etc and /usr (/usr is hard to explain sometimes)

/media contains links to CD drives, USB drives, and other removable media

There are some directories that most people don't really need to mess with. Those are normally /lib, /opt, /proc, /run, /srv, /sys, and /var

The point of this filesystem is to make everything easy to find.

---

### Post by drew14 on 2014-03-16
thank you

---

