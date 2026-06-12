---
title: "Help! I need to reset my password for version 16.04"
date: 2017-11-08
forum: General Help
---

### Post by WA4MOE on 2017-11-08
I also have suddenly recd "invalid Password". Reset using recovery mode in 16.04.

 Used Command at root; passwd username

Changed pw to new one....confirmed....

Still notable to log in...Same message"Invalid Password"
Please
Moe

---

### Post by deadflowr on 2017-11-08
Moved post to it's own thread
from here: [https://ubuntuforums.org/showthread.php?t=2374985]("https://ubuntuforums.org/showthread.php?t=2374985")

When using recovery mode to reset a password you need to re-mount the file system read/write.
recovery mode sets it read only so any changes made will get wiped out at reboot.
Either use the Enable networking feature in recovery mode, (this option resets the file system as well as enables networking)
or run
```
 mount -o rw,remount /
```
this will remount the file system read/write and allow password changes to remain after reboot.

---

