---
title: "howto: reset UUID"
date: 2006-10-14
forum: General Help
---

### Post by carolinason on 2006-10-14
How does one go about resetting UUID's when they change? Or should I just revert fstab to the /dev/hda*, /dev/sda* nomenclature? ](*,)

---

### Post by kidders on 2006-10-14
Hi there,

If your filesystem UUIDs are prone to changes, you should use the /dev/xxxx style device paths in /etc/fstab. The main idea behind label/UUID-based device naming conventions is that, should something fundamental about a filesystem change, Ubuntu won't just carry on treating it as if nothing had happened.

I suppose the idea is that Ubuntu would "notice" that you'd formatted a partition, say, or replaced it with a new physical device, and refuse to just assume you wanted it mounted with the same parameters & mount point as before. If you can't think of a reason why you'd want your box to behave that way, you should refer to your hard disks by name.

Incidentally, afaik there's no reason why you can't mix & match device name styles in your /etc/fstab.

Hope that helps.

---

### Post by carolinason on 2006-10-15
Thank you, the original fstab nomenclature works. I appended my root partition in gparted to make it larger. This changed the UUID.

---

