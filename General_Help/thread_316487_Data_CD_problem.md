---
title: "Data CD problem"
date: 2006-12-10
forum: General Help
---

### Post by cgrenier on 2006-12-10
I have a problem with data and music CDs: they don't work.  Nothing mounts, I can't read them.  This is weird because DVDs work fine in the same drive, I can read them and burn them, both pressed and burned DVDs.  CDs on the other hand don't seem to be readable.  When I'm in Windows on the same machine, they work fine.

My fstab has this line:

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

When I put in a data CD with 3 files on it, and then type "file /dev/hdb", I get "/dev/hdb: block special (3/64)" .  So it reads my disc enough to detect that it has 3 files on it.

When I do "sudo mount -t iso9660 /dev/hdb /media/cdrom0" I get "mount: No medium found"

If I take out a CD and put in a DVD, everything suddenly works fine and the DVD is perfectly readable and mounted at /media/cdrom0 .

I am completely baffled.  I know the discs work fine on other computers and on windows, and the drive works fine in Windows and with DVDs.

Any help would be appreciated...

--CG

---

