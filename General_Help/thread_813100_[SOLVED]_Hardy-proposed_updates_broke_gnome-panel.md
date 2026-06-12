---
title: "[SOLVED] Hardy-proposed updates broke gnome-panel"
date: 2008-05-30
forum: General Help
---

### Post by edantes on 2008-05-30
Earlier today I installed a number of updates from the Ubuntu servers.

I had forgotten the "Pre-released" option checked in the updates configuration and the process installed a number of packages from the Hardy-proposed channel, removing obsolete and incompatible ones. 

Cutting the story the story short, gnome-panel was removed  (an error in the dependencies of the new gnome-desktop-data, I think)

Question: Is there an easy way of backtracking the changes made from the Hardy-proposed channel?

---

### Post by WRDN on 2008-05-30
You could try uninstalling the one you currently have, and installing the latest stable version. 

For the record, im using gnome version 2.22.2

---

### Post by edantes on 2008-05-30
Thanks for your reply.

I was hoping there would be an automatic way of downgrading all packages in that unfortunate update.

I did it by hand for all "gnome-*" packages installed from Hardy-proposed.  There were quite a few other packages in the upgrade, including Compiz and OpenOffice.   I still have a mess in my upgrade status reports and some gnome panel applets not working.
 
I am also running gnome 2.22.2.  This latest batch of updates take some pakages from 2.22.2.1 to 2.22.2.2.

I will wait and see if the problems work themselves out with fixes in the update channels.

---

### Post by edantes on 2008-05-30
It turns out my first update attempt  removed packages that depended on gnome-panel, which was incorrectly removed by the new gnome-desktop-data (my guess).  Whatever the reason, it got fixed in my new installation from the same hardy-proposed update channel.  In my case, the damage was done and I had to reinstall some of these removed packages manually.

---

