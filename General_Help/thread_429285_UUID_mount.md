---
title: "UUID mount"
date: 2007-05-01
forum: General Help
---

### Post by mattmole on 2007-05-01
Hi,

I was wondering if someone could explain to me why since edgy in the fstab file harddrives are mounted by a UUID. To me, this is unnecessary as I can look at the partitions on my drive and easily mount /dev/hd[a-z][0-9]. I realise now that I can look in /dev/harddrive/uuid/ (or similar) and see which drive each UUID is symlinked too, but is there another way and why was the change felt necessary?

Cheers, mattmole

---

### Post by mcduck on 2007-05-01
> **mattmole said:**
> Hi,

I was wondering if someone could explain to me why since edgy in the fstab file harddrives are mounted by a UUID. To me, this is unnecessary as I can look at the partitions on my drive and easily mount /dev/hd[a-z][0-9]. I realise now that I can look in /dev/harddrive/uuid/ (or similar) and see which drive each UUID is symlinked too, but is there another way and why was the change felt necessary?

Cheers, mattmole

The problem with using device names in fstab is that if you move a drive to another cable, it's device name changes. Also removable drives device names change depending on which order thay are plugged in (or recognized while booting). UUID instead will always stay the same.

---

### Post by mattmole on 2007-05-01
Hi,

Thanks for the response. It makes a lot of sense then that the UUID stays the same no matter what the /dev/... becomes. How are the UUID generated?

Matt

---

### Post by mcduck on 2007-05-01
> **mattmole said:**
> Hi,

Thanks for the response. It makes a lot of sense then that the UUID stays the same no matter what the /dev/... becomes. How are the UUID generated?

Matt

I believe that the UUID is just randomly generated, and then assigned to the partition when the partition is created. (or when you are installing/upgrading Ubuntu 6.10 or later if your partitions don't already have UUID's assigned to them).

So, if you edit your partitions they will get new UUID's and you need to also edit fstab to reflect the change.

I think it's also possible to change the UUID, if you for some reason would need to.

So, the point is just that the UUID is unique, it doesn't actually matter what the UUID is.

[http://en.wikipedia.org/wiki/UUID]("http://en.wikipedia.org/wiki/UUID")

---

