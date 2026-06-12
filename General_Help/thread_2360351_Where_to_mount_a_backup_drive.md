---
title: "Where to mount a backup drive"
date: 2017-05-03
forum: General Help
---

### Post by claudedjones on 2017-05-03
I'm interested in having a backup drive that is not part of my home directory - it will be primarily used to backup my home partition. Where should I mount to follow best practices? Or, am I thinking about this incorrectly?

---

### Post by ajgreeny on 2017-05-03
Is this an internal or external drive?

If internal the normal place to mount it would be /mnt and then make the disk available to you as a user by changing the permissions of its partition with a **chmod** command and/or a **chown** command to change ownership.

Come back again if you need more info on this.

---

### Post by Habitual on 2017-05-04
Claude:

Here's my approach, right or wrong, it's how it has worked here for years.

Internal disks, or "fixed" or permanent should be in /etc/fstab and will mount where told.
I use /etc/fstab for fixed assets that reside as part of the system.
Static perms:owner:group permissions are bare-bones (as seen by the system) or "No users here"
Managing perms:owners in this fashion soon becomes tedious, IMO.
This becomes a nightmare for the SysAdmin (you).

Let me show you another way...

External media I mount using
```
/usr/bin/udisksctl mount -b /dev/sdc1 /media/jj/**[COLOR="#FF0000"]external [/COLOR]** > /dev/null 2>&1
```
and the owner:perms remain.
**NOTE**: the directory _external_ in the example here is completely arbitrary and does not have to exist prior to mounting.
It could just as well be /media/claude/<anything_you_choose> Go wild'ish. :)
I have not touched /media/jj/ in any way up to this point.

If the media is "removable" or "not a fixed asset", [the man page for udisksctl]("http://manpages.ubuntu.com/manpages/trusty/man1/udisksctl.1.html") says /media/ is the place.

Here's my Down and Dirty  script I use 10 times a day:
```
#!/bin/bash
cd $HOME; sync
/usr/bin/udisksctl mount -b /dev/sdc1 /media/jj/external  > /dev/null 2>&1
ionice -c 3 rsync -azv  . /media/jj/external/ --delete
#EOF
```

Using this script leaves the media mounted.

I hope this helps.

---

