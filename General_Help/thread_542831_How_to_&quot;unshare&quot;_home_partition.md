---
title: "How to &quot;unshare&quot; /home partition ?"
date: 2007-09-04
forum: General Help
---

### Post by PaulFXH on 2007-09-04
I've just installed three Linux OSes (including Ubuntu) on my new laptop.
However, I decided to share not just the Swap partition between the three OSes but also the /home partition which seems to have been a mistake (for example, changing Desktop wallpaper on one OS automatically changes it on another).
So, how can I extricate myself from this by, for example, keeping the /home for just one OS and leaving the other two to have all their home stuff on the root partition.
Obviously, I can do this by re-installing everything. But, is their a less painful option?

---

### Post by frank95com on 2007-09-04
This is normal, expecially if the three system have all the same window manager. This is not simple because if you create an home directory into the root partition of the three system and change the $PATH the folders will remain without any files.

---

### Post by PaulFXH on 2007-09-04
Yeah, actually two of the OSes were using GDM and the other had KDE. Only the two with Gnome seemed to have a problem with "intermingling" of /home files.
OK, looks like I've got some re-install work ahead of me.
Thanks for your comments.

---

### Post by vanadium on 2007-09-04
It principle, it is possible to move the home of a user. You must then be operating under another account (with root privileges), move the users data and change the settings of his account to reflect the new location. The "usermod" does that.

---

