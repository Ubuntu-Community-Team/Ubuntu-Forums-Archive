---
title: "Unable update"
date: 2023-01-27
forum: General Help
---

### Post by hezy2 on 2023-01-27
Hello,
cannot update. See screenshot:
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291639&stc=1[/IMG]
thanks,
Hezy

---

### Post by josefranw on 2023-01-27
That happens when two package managers are running at the same time. You need to make sure no other package manager or updater is running when trying to run sudo apt update from the terminal. Sometimes, it also means that the system is running a "background update". In other words, you can't run updates at the same time...

---

### Post by hezy2 on 2023-01-27
Thanks

---

### Post by ActionParsnip on 2023-01-27
If a GUI app like software centre is open, close it (if it is idle) then retry. If you have ran updates in another terminal then let that finish and retry. If this doesn't help then reboot. If this doesn't resolve the issue then let us know and we can unlock the packages for you

---

