---
title: "losing /dev entries"
date: 2007-12-05
forum: General Help
---

### Post by Rod S on 2007-12-05
First off, the problem is occuring on a debian testing system.

hardware: four ide drives (hda -hdd); two sata drives (sda & sdb)

Problem: my thumbdrive usually mounts on /dev/sdc1as specified in my fstab file but I keep losing the sdc entries in /dev. I get a warning: "block special device not found" error then I have to recreate the /dev/sdc entries using mknod. Has anyone here experienced this problem? If so, have you found the cause or a solution. 

Thanks in advance for any input.
Rod

---

