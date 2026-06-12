---
title: "Need help with terminator!"
date: 2008-06-12
forum: General Help
---

### Post by juanmanuelagueda on 2008-06-12
Can someone help me to customize terminator?

I have just installed it, and all the colors are very dark and Im not able to read anything!

Thanks in advance!

---

### Post by qhaz on 2008-07-08
Firstly, I'd suggest grab the latest stable release.
Add this line to your /etc/apt/sources.list

deb [http://ppa.launchpad.net/gnome-terminator/ubuntu](http://ppa.launchpad.net/gnome-terminator/ubuntu) hardy main restricted universe multiverse

The latest release has a lot of new features.
Configuring Terminator can be done by right mouse clicking in terminal window and selecting options there.  Or, by creating/editing 

~/.config/terminator/config

I needed to create this file myself.
Options that can be put in this file can be found by reading

man terminator_config

cheers

---

