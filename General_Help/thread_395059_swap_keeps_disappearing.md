---
title: "swap keeps disappearing"
date: 2007-03-27
forum: General Help
---

### Post by superspak on 2007-03-27
ok, so i got my swap to work, and now whenever i shut down, when i start back up again, it says that its an unknown partition so i have to reformat it to a swap and use swapon, how to get it to remember the swap partition?

---

### Post by kpkeerthi on 2007-03-27
What is in your /etc/fstab?

---

### Post by superspak on 2007-03-27
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=b6b12adf-229f-440c-bb4c-c9a180e99d26 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=d08ba457-1c58-4cb5-9793-d4cd4fc69ac3 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3           swap    sw              0       0

---

### Post by superspak on 2007-03-28
ok, so i searched on google for an answer, and i put in the correct fstab line, but now when i start up, it says "activating swap    [FAIL]" not sure whats wrong

---

