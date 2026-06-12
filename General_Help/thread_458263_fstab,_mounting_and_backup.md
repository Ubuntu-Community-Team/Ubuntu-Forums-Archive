---
title: "fstab, mounting and backup"
date: 2007-05-29
forum: General Help
---

### Post by sanoj on 2007-05-29
Fellow Ubuntians,

I have a problem with dismounting my backup device (/dev/hdb1) at /media/backup as a regular user. The entry in /etc/fstab looks like this:

```

UUID=383c6bd9-7543-4071-a43d-2173f4b22943 /media/backup   ext3    data=journal,noauto,user        0       2

```

I can properly mount this as a regular user, but I can not umount it. Trying to umount it gives me the following message (translated from my native language to English by myself):

```

umount: mounting of /media/backup does not match fstab

```

Typing *mount* gives me this:

```

/dev/hdb1 on /media/backup type ext3 (rw,noexec,nosuid,nodev,data=journal,user=jonas)

```

Umounting with *sudo* works alright. 

I guess I should also add that replacing the UUID-string in fstab with the device name seems to work, however, I am not sure that is the correct solution (by the way, does it break anything?).

---

### Post by hasimir44 on 2007-05-29
I was about to say "where'd you get that UID string?" until I checked my /etc/fstab and found that I have the same type of strings.. I've never seen these before. Can someone post a short explanation of what these strings are and how they're used? 

sorry I don't have an answer, but I'm interested too, so I bumped.

---

### Post by fanatik on 2007-05-30
well i believe that they are there to protect against if the device name should ever change, the UUID won't so you'll still be able to mount your filesystems. you can see all your UUID's for your partitions by typing **blkid** in a terminal. mine were converted to UUID's when i upgraded to edgy.

i don't have an answer to sanoj's problem either, sorry.

---

