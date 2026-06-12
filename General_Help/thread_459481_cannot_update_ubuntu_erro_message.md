---
title: "cannot update ubuntu erro message"
date: 2007-05-30
forum: General Help
---

### Post by akilarules on 2007-05-30
when i try to update ubuntu it the update manager finds all the new updates and when i try to install them an error message pops up saying the following: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i went into terminal and ran dpkg --configure -a it said i needed superuser privileges, even tho i am the computer administrator. what do i do?

---

### Post by gmmazlum on 2007-05-31
I´ve got this error when updating manager
[I]
"Could not initialize the package information"

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Dynamic MMap ran out of room, E: Dynamic MMap ran out of room, E:Error occurred while processing libsctp-dev (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/ftp.debian.org_dists_sarge_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'[/I]

Then I cant update

---

### Post by happy-and-lost on 2007-05-31
*sudo dpkg --configure -a*

---

### Post by gmmazlum on 2007-05-31
Thanks

I just removed the "Third-Party Software" list that was crashing de updater

---

