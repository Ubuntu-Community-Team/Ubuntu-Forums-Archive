---
title: "How to disable automount of a network share but still show its mount in file manager"
date: 2014-10-12
forum: General Help
---

### Post by Ev1L on 2014-10-12
Hi,
I added a ntfs network share to fstab and it automounts correctly and shows the link in file manager.
Is it possibile (perhaps with some fstab parameter) to disable mount at boot but still have its link in file manager?
For example like some windows partition I see in Devices but are not mounted until I click them (however they are automatically found without being in fstab).

Thanks

---

### Post by mcduck on 2014-10-12
just add "noauto" in the mount options. (and "user" as well if you don't have it already, to allow normal users to mount the drive).

Another option is of course to not have it in fstab and instead just connect to it using the file manager's own network connections feature, and then bookmark the location.

---

### Post by TheFu on 2014-10-12
Or use the **autofs** method. It is more complex and the storage won't show up anywhere until accessed.
You probably want the method mcduck suggests.

---

### Post by Ev1L on 2014-10-12
thanks guys, I went for the first suggestion :)
i had the feeling i was forgetting noauto but didn't find it quickly enough.
user, however, i didn't know :)

---

