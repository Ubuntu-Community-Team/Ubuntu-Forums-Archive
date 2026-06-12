---
title: "Two Startup Problems"
date: 2008-04-13
forum: General Help
---

### Post by sekinto on 2008-04-13
Okay, my first one is that I edited my /etc/fstab file to mount my external hard drive's partitions in certain folders. My problem is that if my external drive is not plugged in the boot splash screen stops and it goes into text/verbose mode and tells me to press ctrl-D to continue. Is there any way to make it not mount the drives if they aren't there, without asking me anything?

My second is Firestarter, someone said adding this:
> tony ALL= NOPASSWD: /usr/bin/firestarter 
to my /etc/sudoers file would make Firestarter able to start on startup for me without me needing to type in a password, I did it and when I log in I still get get an "Insufficient Privileges" message.

---

### Post by pointone on 2008-04-13
Try adding the "noauto" option to your external drive's mount options. This will prevent it from being mounted automatically on boot, but when you explicity try to access the drive, it should mount everything correctly.

The Firestarter executable is "/usr/**sbin**/firestarter", by the way.

---

### Post by sekinto on 2008-04-13
Thank you.

---

