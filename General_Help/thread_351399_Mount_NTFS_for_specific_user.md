---
title: "Mount NTFS for specific user"
date: 2007-02-01
forum: General Help
---

### Post by Skidpad on 2007-02-01
All: my laptop has two users, both of which my NTFS partition mounts automatically at login.  I'd like to have it mount **only** for my username - which is the first user created when I installed Edgy.

Based on this thread: [http://www.ubuntuforums.org/showthread.php?t=73365&highlight=mount+user](http://www.ubuntuforums.org/showthread.php?t=73365&highlight=mount+user)
I used sudo gedit /etc/fstab and added my UID as 1000 just before "unmask", but when the other user logs in, the NTFS partition still mounts for them, too.

[B]Here is my current fstab, as returned to original:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=edbb274c-db4f-470b-b65d-8aeb8b9b5575 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=195cee00-b0f7-4e80-b604-bb4a25c1f4e1 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
#
/dev/hda1 /media/windows ntfs umask=0222 0 0[/B]


I've read the "man fstab" and other pages, but I still don't quite get the syntax necessary to only mount this NTFS partition for just my username.

Any input greatly appreciated!

---

