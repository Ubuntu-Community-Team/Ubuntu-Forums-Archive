---
title: "'Permission Denied' for mythtv on external hard disk"
date: 2014-02-07
forum: General Help
---

### Post by jsciak on 2014-02-07
Hi everyone,

I just wanted to share the solution I just found to something that was driving me a little crazy:

In trying to get MythTV on my [FONT=arial, sans-serif]Ubuntu 13.10 distro[/FONT] to record to an external USB drive with an ext4 fs, I chown'd and chmod'd all up and down the storage group's directory structure to no avail. Finally, I noticed a '+' plus sign at the end of the permissions on the mount point's parent directory. A little googling told me that a '+' sign at the end of permissions means that there's an ACL, or access control list on the file/directory. Using getfacl I found that there was no group assigned to the ACL of the directory. I added my MythTV group to the ACL with 'sudo setfacl -m g:mythtv:rwx' and now my MythTV user can write to my external hard disk! Huzzah!

Cheers,
Jonathan

p.s. - The MythTV group will still need standard directory/file access to the recordings directory (chgrp mythtv /your/mythtv/recordings;chown g+w /your/mythtv/recordings).

---

### Post by gphonesethlang on 2014-12-20
Just to confirm for anyone else looking for the same info: the above instructions also fix the problem for Debian Jessie.

---

