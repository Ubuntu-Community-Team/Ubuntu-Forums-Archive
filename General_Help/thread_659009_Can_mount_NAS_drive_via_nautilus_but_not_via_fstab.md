---
title: "Can mount NAS drive via nautilus but not via fstab"
date: 2008-01-05
forum: General Help
---

### Post by Jahkel on 2008-01-05
Hey all,

I have just noticed that my NAS drive mount points in fstab have suddenly stopped working.  I can mount the folders via using nautilus, but I need to use proper mount points so that I can get programs like Exaile to see my music etc.

My fstab lines look like this:

```

//jenova/media	/mnt/media	cifs	default,rw,username=andy,password=	0	0

```

However, I can the error that "jenova" cannot be resolved.  Using the IP address instead says that the address is unreachable - I can't even ping it.  Yet, the smb mount method works fine via nautilus?!

Any help welcome, so I can get back to listening to a little music again!

---

### Post by pietjanjaap on 2008-01-05
Goto "system-administration-storage device manger", there you can change it.

---

### Post by Jahkel on 2008-01-05
Huh?

---

