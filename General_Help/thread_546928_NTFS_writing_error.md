---
title: "NTFS writing error"
date: 2007-09-09
forum: General Help
---

### Post by s-lime on 2007-09-09
I followed tutorial to setup **ntfs-3g** here:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

I have a link in **Applications > System Tools**. I enabled support for external device (the only one option available.) 

But when I look at my NTFS disk properties, the owner's permission is set to read. If I try to change it to Read and write, it displays:

**The permissions could not be changed.**
Sorry, couldn't change the permission of "Projects".

What am I doing wrong?

Thanks for every answer. Really.

---

### Post by vanadium on 2007-09-09
I also experienced nautilus behaving a bit weird immediately after installing ntfs-3g. I could not create new files or folders in the root directory of the mounted drive in the regular way (file -new). However, dragging to the drive would work. Subdirectories worked as expected. 

Anyway, check with the "mount" command that your drive is mounted with ntfs-3g, and not regularly with ntfs. Before taking any actions, restart the system and see wheather the issue still exists.

---

### Post by s-lime on 2007-09-09
Still exists after restart. Could you please tell me how to mount it with ntfs-3g and not with ntfs?

Thanks for your answer.

---

### Post by s-lime on 2007-09-09
anyone?

---

### Post by merlinus on 2007-09-09
Post results of:

```

sudo fdisk -l
cat /etc/fstab

```

---

