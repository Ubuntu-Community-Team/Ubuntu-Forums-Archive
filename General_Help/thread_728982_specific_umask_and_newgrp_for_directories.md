---
title: "specific umask and newgrp for directories"
date: 2008-03-19
forum: General Help
---

### Post by bukharin on 2008-03-19
Hi all.

I have a simple two partition setup, with one partition for / and another for all data (photos, music, video, etc) called simply "vault". All data in vault *should* be readable and writable by all members of group "vault", and all files and directories should be owned by this group.

Evidently, this can be acomplished by 
$ chgrp vault file
$ chmod 775 file

but this is cumbersome, and slow.

i thought of using umask and newgrp to set up this options, but this won't work as they are 1.- per user and 2.- system-wide. This has to affect all users (or all members of a group), in a particular directory (including all subdirectories, and wishfully, excluding simlynks).

Is there a way to enforce a specific owner, mode and group for all files created by any user in a given directory and subsequent subdirectories?

Any help would be greatly apreciated.

Thanks!

---

### Post by jrib on 2008-03-19
I believe you can do this with Access Control Lists (ACL). getfacl and setfacl are the two shell commands you use (after you enable acl in your fstab options). eiciel is a graphical editor for ACLs if you prefer.  I don't really know of good documentation other than the man pages for the two commands above and this page in my bookmarks: [http://wiki.kaspersandberg.com/doku.php?id=howtos:acl](http://wiki.kaspersandberg.com/doku.php?id=howtos:acl)

---

