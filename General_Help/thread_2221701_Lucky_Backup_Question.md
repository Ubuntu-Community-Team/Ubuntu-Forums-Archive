---
title: "Lucky Backup Question"
date: 2014-05-03
forum: General Help
---

### Post by dtree46 on 2014-05-03
Could Lucky Backup be used to 'clone' a system?
I use it now to automactically backup /home daily.
Would it be possible to do a / /dev/sdc1 weekly?
Would that work?

dlw

---

### Post by ibjsb4 on 2014-05-03
LuckyBackup is a GUI for Rsync and rsync can clone.

[https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)

Myself I rarely clone and find it easier just to use clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by dtree46 on 2014-05-04
Thanks for replying.
My goal is to do an incremental clone weekly.
I do a daily of 'home' now.
This way I would loose nothing. Hopefully!

dlw



> **ibjsb4 said:**
> LuckyBackup is a GUI for Rsync and rsync can clone.

[https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync](https://wiki.archlinux.org/index.php/Full_system_backup_with_rsync)

Myself I rarely clone and find it easier just to use clonezilla.

[http://clonezilla.org/](http://clonezilla.org/)

---

