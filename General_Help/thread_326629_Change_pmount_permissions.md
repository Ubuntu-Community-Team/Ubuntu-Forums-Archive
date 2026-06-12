---
title: "Change pmount permissions"
date: 2006-12-27
forum: General Help
---

### Post by jeelliso on 2006-12-27
Hello,

I have a new Seagate 200GB external hard drive that I have formatted with ReiserFS.  When the drive is plugged in, Gnome automatically mounts it using pmount (I believe).  The problem is it is mounted with root permissions instead of normal user permissions.  Since pmount is supposed to allow normal users to mount/unmount removable devices, I would like to change these permissions by default.  I've come across a very similar thread, but there was not solution found in that thread, so I'm posting this one.

Other info:  I don't want to have the drive mounted all the time (it is on a laptop) so adding anything to /etc/fstab is out of the question.  I'm using Ubuntu 6.10 fully updated.

Thanks,
~Justin

---

