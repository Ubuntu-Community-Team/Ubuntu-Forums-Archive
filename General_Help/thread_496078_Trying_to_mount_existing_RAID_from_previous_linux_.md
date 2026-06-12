---
title: "Trying to mount existing RAID from previous linux system"
date: 2007-07-08
forum: General Help
---

### Post by user5001 on 2007-07-08
I am trying to mount a RAID level 1 (two disks) that I used on my previous linux system.  Please note, I am just using it as a secondary drive for backup purposes.  No other RAIDs exist on my Ubuntu system.  I have copied the information from the raidtab file into a new /etc/raidtab file on my Ubuntu system.  I added the appropriate fstab line, and added md and raid1 to the modules file.  I ran MAKEDEV md, and then rebooted the system.  The drive did not mount, so I tried manually with a mount command, and it told me that the /dev/md2 file was missing.  I ran MAKEDEV md again, and realized that it placed the files in the /dev/.static/dev folder.  So, what am I supposed to do to get it to create them in the /dev folder.  And, is there anything else I need to do?

Thanks,
Jason

---

### Post by bettlebrox on 2007-07-08
Do you have the appropriate raid modules and the md module loaded?

---

