---
title: "Fun with Gnome 2.11 Apps"
date: 2005-07-13
forum: General Help
---

### Post by SpEcIeS on 2005-07-13
Lately I have been applying some of 2.11 updates, which most work fine. However, sometimes I run across this error in my packaging:
[b][i]
(Reading database ... 185483 files and directories currently installed.)
Preparing to replace gnome-terminal 2.10.0-0ubuntu2 (using .../gnome-terminal_2.11.1-1_i386.deb) ...
Unpacking replacement gnome-terminal ...
dpkg: error processing /home/species/Downloads/gnome-terminal-2.11.1/gnome-terminal_2.11.1-1_i386.deb (--install):
 trying to overwrite `/usr/var/scrollkeeper/C/scrollkeeper_cl.xml', which is also in package file-roller
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /home/species/Downloads/gnome-terminal-2.11.1/gnome-terminal_2.11.1-1_i386.deb
[/i][/b]
Now, obviously file-roller had no problems, however after building gThumb 2.6.6, which runs just fine as an installed app, will not install as a deb package. Before doing so, should I remove the _/usr/var/scrollkeeper/C/**scrollkeeper_cl.xml**_ ?  :?

_Update:_
Bluefish 1.0.2 had some complaints also, however gnome-terminal 2.11.1 does work a little quicker than the previous version. This was not a deb package though. Same problem still exists. :(

---

