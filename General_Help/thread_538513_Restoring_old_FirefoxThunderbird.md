---
title: "Restoring old Firefox/Thunderbird"
date: 2007-08-30
forum: General Help
---

### Post by mertle on 2007-08-30
I recently had to repartition my HD and seem to be having a problem in restoring the backups of my Firefox and Thunderbird settings/bookmarks/email/etc. I've followed the directions in Mozilla's FAQ as well as numerous posts on here, but to no avail.

In the past, all that had to be done was copy the backed up profile folder from my old /home dir into the new one, launch the program, and all was as it was. Now, all I get is an error message telling me that the program's process (both FF and TB) is already running and I must exit said process before launching another instance.

Perhaps this is a locked file/permissions issue? I dunno, it's aways worked right as rain when I've done this before.

Thanks in advance for any aid.

- mertle

---

### Post by Delkster on 2007-08-30
Try going to ~/.mozilla/firefox/, find your profile directory there, and enter that directory. It'll be an interesting combination of alphanumeric characters, e.g. ~/.mozilla/firefox/duh6k4l8.default or something similar. See if there's a file (or symbolic link) called "lock" there, and remove it if it exists.

Thunderbird has a similar lock file in ~/.mozilla-thunderbird/crypticprofileid.default/lock.

---

### Post by ajgreeny on 2007-08-30
If you have a copy of the whole of the old **/home/username/.mozilla-thunderbird** and **.firefox** folders, both hidden, replace that, not just the profile or you will have problems of the **profiles.ini** pointing to the wrong profile.  Alternatively just edit the **profiles.ini** to make sure the alphanumeric of the default is correct for your profile, and not still pointing to the wrong one.

---

