---
title: "Forgot to unmount flash drive and now it's read-only :("
date: 2008-04-27
forum: General Help
---

### Post by Envergure on 2008-04-27
I removed my flash drive without unmounting and now it's read-only.  How do I fix this?

---

### Post by GenericGuy on 2008-04-27
Do you have a windows box handy?

If you do, just plug in the drive and run scandisk on it, it worked for me
And if someone has a better (or more Ubuntu friendly) solution please post it, I also want to know.

---

### Post by ryanhaigh on 2008-04-28
What filesystem is used on the usb drive? Do you see any related error messages in the system log (system>admin>logs)

---

### Post by Envergure on 2008-04-28
No fatal errors.  The file system is called "vfat".

I haven't done anything yet, but it's started working again now.  I just plugged it into a different USB port this time and it stopped complaining.

---

### Post by cb951303 on 2008-04-28
I'm not sure but if that happens again you can try to force mount the drive.

it worked for me with a ntfs usb disk

---

