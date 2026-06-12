---
title: "File Size Limit Exceeded"
date: 2006-09-06
forum: General Help
---

### Post by hiptahop on 2006-09-06
I can't create a file larger than 4GB.  I suspect I may need to alter the mount options.  Atm, the device is mounted as follows:

/dev/hdb1  /mnt/Disk1  vfat  iocharset=utf8,umask=000  0  0

---

### Post by orb9220 on 2006-09-06
Nope that is the limatation of fat32 you can have no single file larger than 4gb in size. 

I ran into this problem with dvdshrink ripping movie to my  fat32 as an iso to get around this I had to tell shrink to save as file structure instead of iso.

---

