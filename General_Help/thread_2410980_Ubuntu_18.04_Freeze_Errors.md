---
title: "Ubuntu 18.04 Freeze Errors"
date: 2019-01-23
forum: General Help
---

### Post by ianneil on 2019-01-23
Ubuntu 18.04 freezes frequently on my laptop especially when i am using chrome or visual studio code. Then the screen below appears:
[ATTACH=CONFIG]282281[/ATTACH]

When i press the power button, i get this added info on the screen:
[ATTACH=CONFIG]282282[/ATTACH]


When i press the power button for long and the laptop restarts, i get this screen
[ATTACH=CONFIG]282283[/ATTACH]

Please help. I don't know what is going on and it is really frustrating. Thank you for your time

---

### Post by DuckHook on 2019-01-23
Welcome to the forums, ianneil.

Based on the first screenshot, your HDD may be on its last legs. There is a high likelihood that your file structure is corrupted at any rate. Note the references to bad superblock, I/O errors, etc.

First backup all critical data.

After successfully backing up, then try fixing your file system with *fsck*. A good set of instructions here: [https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/](https://www.tecmint.com/fsck-repair-file-system-errors-in-linux/)

Even if this fixes the issue, you need to be careful about this HDD. Try running a series of disk health checks. Maintain good backups just in case.

---

### Post by ianneil on 2019-01-23
Thank you. I will follow the instructions and give you feedback

---

### Post by DuckHook on 2019-01-23
It hardly needs saying, but remember to backup all data before doing anything else. You don't want to put yourself in a position of having to recover a nuked drive.

---

