---
title: "The mtab file."
date: 2008-07-02
forum: General Help
---

### Post by McTek on 2008-07-02
What file rewites the mtab file when the system is rebooted?
When I edit mtab it is rewritten on reboot. Anyone have a clue.

---

### Post by ibutho on 2008-07-02
mtab should be rewritten at boot time. It reflects the contents of /proc/mounts i.e. devices currently mounted on the system.

---

### Post by sdennie on 2008-07-02
If you are trying to edit your mounts, the file you want to edit is /etc/fstab.  As ibutho said, /etc/mtab is just a status file.

---

