---
title: "Treo650 Sync freezing on ToDo"
date: 2007-04-24
forum: General Help
---

### Post by tonymccallie on 2007-04-24
I just installed Feisty and love it. I wanted to sync my Treo650 with evolution. I Added the device using the new usb: as opposed to the old /dev/ttyUSB1 and it works brilliantly except for ToDo. When I hot sync, everything works as advertised until it gets to the ToDo list. It just hangs. If I `killalll gpilot-applet` and remove that conduit, the sync runs all the way successfully. I tried to set the conduit to 'Copy from PDA' with no difference, even after purging the completed items off the Treo. I also tried creating a new Task category and syncing with it in case it was a file problem in evolution. Still no joy.

Any ideas?

Blessings, Tony

---

### Post by naked on 2007-04-25
Same problem with a 680 and Feisty.

Any help?

L

---

### Post by naked on 2007-04-25
I found this bug report:  [https://bugs.launchpad.net/ubuntu/+source/gnome-pilot-conduits/+bug/81170](https://bugs.launchpad.net/ubuntu/+source/gnome-pilot-conduits/+bug/81170)

Unfortunately, looks like this has been around since January.  

I'll post back if I find anything.

L

---

