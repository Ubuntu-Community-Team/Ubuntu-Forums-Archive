---
title: "CD drive unable to mount"
date: 2007-04-24
forum: General Help
---

### Post by NotoriousTF on 2007-04-24
Hello all!

Last week I upgraded to Fiesty, and so far I've encountered few problems. I had a resolution problem which I got sorted, and a few graphics card issues which are also done & dusted now.
This morning I stuck a data CD into the drive and an error box popped up:

[B]
Cannot mount volume.[/B]
Unable to mount the volume.
>Details
[mntent]: line 10 in /etc/fstab is bad
mount: can't find /media/cdrom0 in etc/fstab or etc/mtab

I've had a search around the forums and so far I haven't found anything of use. I run a dual boot, so I tested the CD drive in XP and it worked perfectly. I should add that the CD image doesn't appear on the desktop when the CD is inserted either.

Anyone out there have any ideas on what I can do to remedy the problem?

**Resolved**
Ended up messing around with the fstab file, namely the line which mentions the cd drive and eventually sorted it out!

---

