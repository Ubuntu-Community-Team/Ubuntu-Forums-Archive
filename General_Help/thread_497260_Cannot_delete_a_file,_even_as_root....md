---
title: "Cannot delete a file, even as root..."
date: 2007-07-10
forum: General Help
---

### Post by smartboyathome on 2007-07-10
Ok, I was running UCK (Ubuntu Customization Kit) to try to see if it would customize my friend's debian-based ISO when the space on my drive got filled up. The first thing I deleted was all the files that UCK created. When I tried deleting the squashfs-source file, it wouldn't let me (keep in mind this was in a nautilus session run from a root terminal). I tried changing the permissions so all users in the root group could delete files, when it said that the filesystem it was on was read-only (even though I know better). I then tried removing it via rm -R /home/aabbott/tmp/squashfs-source, and it spit out "rm: cannot remove 'file':read-only file system" (keep in mind, I am still in a root terminal). The reason I am so determined to delete this file is because it takes up 2 GB (and on my 20 GB ubuntu install, that is a lot). Anyway, how would I go about removing this file?

---

### Post by Jordan777 on 2007-07-10
I'm not sure what being the root is but gksudo nautilus has always worked for me.

---

### Post by smartboyathome on 2007-07-10
same thing basically (gksudo is a graphical version of sudo, which allows a command to be runs as a super-user [root]). Anyway, it still doesn't work.

---

### Post by Adramelech on 2007-07-10
r u trying to deleted a file from a live cd? reboot it should be gone

---

### Post by yopnono on 2007-07-10
You need to unmount it *not delete* it  'file':read-only file system"

---

### Post by CrankyFilipino on 2007-07-10
> **Jordan777 said:**
> I'm not sure what being the root is but gksudo nautilus has always worked for me.

Thanks.. I was searching the forums and this is exactly what I needed :)

---

### Post by smartboyathome on 2007-07-10
> **yopnono said:**
> You need to unmount it *not delete* it  'file':read-only file system"

> **Adramelech said:**
> r u trying to deleted a file from a live cd? reboot it should be gone

Ok, I will try rebooting. And it shouldn't be a livecd, after all, I stopped UCK.

---

### Post by Jordan777 on 2007-07-10
Glad I could help with my limited knowledge haha :lolflag:

---

