---
title: "some apps fail to start"
date: 2024-02-29
forum: General Help
---

### Post by xeddog on 2024-02-29
I just had to rebuild an Ubuntu 22.04 machine due to a  lack of disk space on the boot drive.  It was only a 120GB SSD which is plenty to run on, but one of my applications filled it up and brought the machine to a halt (meaning everything PAUSED until space could be freed up).  This app placed a LOT of temporary stuff in the user home directory, and apparently cannot be changed.  The final output of this app is then moved after downloading to a 1TB drive that was in the machine too. In an attempt to resolve this, I replaced the second drive with a 2TB drive because 2 TB is better than 1TB and why not, and mounted it as /Home (Capitalized H), and moved my home directory to it via the usermod command.  All seemed good until I tried to launch Firefox. When I tried to launch it, there was a tab placed in the top bar and the spinny disk icon, then . . . nothing.  It all just went away.  The Ubuntu Software app doesn't launch anymore either, but doesn't put a tab in the top bar.  There may be other apps that don't work either that I just haven't found yet.

Regarding Firefox, Google shows that this is because of the home directory  move as it apparently needs home directories to be located on /home (lower case).  I have tried a couple of the resolutions I found via google but nothing has worked, so I am here to ask the experts for help.    In the meantime, I did get Firefox working, sorta, by creating a .desktop file for it in my .local.share/applications folder.  Maybe I can do the same with Ubuntu Software if I can find the executable for it.

Wayne

One last detail that may or may not be useful, I installed 22.04.4 on this machine which is a very old I-7 920 processor from 2008, and has 16GB ram

---

### Post by TheFu on 2024-02-29
snap packages have hard-coded constraints and only allow /home/{userid} to be used to run any snaps.  Period.  It is not a Unix or Linux requirement. It is a requirement that only Snaps mandate. Attempts to get Canonical's snap team to be more open about where home directories are located have all failed. They don't listen.

Symbolic links and hard links and bind mounts won't help.  The location of home directories must be /home/{username} - period - on Ubuntu systems.

Firefox is a snap package in Ubuntu 20.04 and later.  You don't have to use the snap version. There are how-to guides to get around it, but other snaps will fail to run as well.

---

