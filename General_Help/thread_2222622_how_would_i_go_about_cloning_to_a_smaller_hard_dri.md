---
title: "how would i go about cloning to a smaller hard drive?"
date: 2014-05-07
forum: General Help
---

### Post by Lewis_Robson on 2014-05-07
can i shrink the drive to go from a 500gb to a 120gb? :)

---

### Post by mikewhatever on 2014-05-07
You could resize the partition, if free space allows it, and then clone. If there is no free space, then no.

---

### Post by oldfred on 2014-05-07
I always suggest a new install.
Then you can copy /home so you have your user settings & data.
You may want  a list of installed apps to make it easier to reinstall if you have added a lot of applications.

Is old drive remaining in system? If so any clone will have major issues with duplicate UUIDs and you have to change UUIDs in one or the other and edit fstab & reinstall grub.
If replacing drive the mikewhatever suggestion should work, but if SSD you may also want different settings.

---

