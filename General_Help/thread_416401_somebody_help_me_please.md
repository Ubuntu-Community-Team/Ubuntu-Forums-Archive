---
title: "somebody help me please"
date: 2007-04-21
forum: General Help
---

### Post by ali780 on 2007-04-21
Hi
I have a problem with my package manager.  When I try to run synoptic package manager I face with following error

E: Dynamic MMap ran out of room
E: Error occurred while processing xpilot-ng (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

and after clicking close synoptic close and I could not install nothing
How can I fix this problem?
 Thank you

---

### Post by spin2cool on 2007-04-21
If you had typed the error message into google, you would have seen that the first 3 results list this solution:

open up this file:
```
sudo gedit /etc/apt/apt.conf.d/70debconf
```

and raise the apt-cache limit by editing the line that looks like this:
```
APT::Cache-Limit "20000000";
```

Raise to to 20M or so, save the file and try again.

I have to wonder why you're running out of room, though.  Do you have a ****-ton of sources in your sources.list file?  Can you clean some of them out?

---

### Post by daygoj on 2007-04-21
CAN SOMEBODY HELP ME 2!!!!!! ok,um  HOW DO I DELETE&UNINSTALL STUFF IN MY WINE FOLDER ? i wont to uninstall nero

---

