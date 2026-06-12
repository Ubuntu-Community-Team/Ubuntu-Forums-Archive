---
title: "mount point /media behaviour"
date: 2015-03-30
forum: General Help
---

### Post by Wim_Grandia on 2015-03-30
Hi,

I was wandering what the behaviour is of a mount point.
I've got a nas mounted via fstab to /media/NAS.
On this NAS my backup program stores its archives.
But what happens when the NAS for some reason isn't mounted?
The mount point is still there but nothing is "behind" it..

At the moment du -shx /* learns me that my /media folder is 36k big.
But when i boot the server into root shell (recovery mode, doesn't look like the NAS is mounted then) du -shx /* says that my /media folder is 52Gb!

---

### Post by Wim_Grandia on 2015-03-30
Is it maybe the case that fstab is not run when in recovery mode?
And that when my NAS is not mounted the /media/NAS folder is a local folder, and that this content is masked when the NAS is mounted?

---

### Post by bab1 on 2015-03-30
> **Wim_Grandia said:**
> Is it maybe the case that fstab is not run when in recovery mode?
And that when my NAS is not mounted the /media/NAS folder is a local folder, and that this content is masked when the NAS is mounted?
Yes.  The mounted partition always hides any data that is in the folder that is used as a mount point.

---

