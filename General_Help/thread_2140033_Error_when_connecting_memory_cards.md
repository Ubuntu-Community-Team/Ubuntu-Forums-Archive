---
title: "Error when connecting memory cards"
date: 2013-04-28
forum: General Help
---

### Post by TimEnid on 2013-04-28
This is what i get when i plug in my camera or take out the memory card and place it in the pc. I am unable to view the contents.

Error mounting /dev/sdm1 at /media/tim/4270-7739: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdm1" "/media/tim/4270-7739"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

any suggestions?

---

### Post by Cheesemill on 2013-04-28
Ubuntu isn't allowed to include exFAT drivers as it is a proprietory Microsoft technology. You can run the following commands to add exFAT support to your system...
```
sudo add-apt-repository ppa:relan/exfat
sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils
```

---

### Post by TimEnid on 2013-04-28
> **Cheesemill said:**
> Ubuntu isn't allowed to include exFAT drivers as it is a proprietory Microsoft technology. You can run the following commands to add exFAT support to your system...
```
sudo add-apt-repository ppa:relan/exfat
sudo apt-get update && sudo apt-get install fuse-exfat exfat-utils
```
I did that. rebooted and i still get the message

---

