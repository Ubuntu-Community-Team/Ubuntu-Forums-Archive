---
title: "[SOLVED] Corrupted /fstab"
date: 2008-06-19
forum: General Help
---

### Post by mandrill on 2008-06-19
Added the dev/hdb1 line last night, all was well, booted this morning, very slow, then verbose, telling me I have errors on lines (I think)  4,5,6....I didn't touch them....

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/hda5
UUID=98a5cae6-3135-47c4-9348-a51d556cc7a1  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/hda6
UUID=238a6627-acb9-4d68-9ec3-7b7bd224e5a1  /home          ext3         relatime                    0  2  
# /dev/hda7
UUID=223738e1-b389-4b42-8516-15f358466708  none           swap         sw                          0  0  
/dev/hdc                                   /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0 

/dev/hdb1   /media/hdb1   vfat      user,auto,fmask=0177,dmask=0077,uid=1000                       0  0
 

Anyway, I can't see anything wrong - so that's why the post. Thanks for any help - I just got this system to where I want it, do not feel like doing a fresh install!

edit: It was line 14 (not 4,5,6 - bad eyes!) the last line (yep, it was me) so I just moved it up next to the rest of the lines and now its happy.

---

