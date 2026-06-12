---
title: "fail to start user manager for uid 120"
date: 2021-09-19
forum: General Help
---

### Post by sdcvs2020 on 2021-09-19
I can't get into the system after giving /USR folder 774 permissions&#12290;
fail to start user manager for uid 120
SEE 'systemctl status [email]user@120.serice[/email]' for details

---

### Post by Impavidus on 2021-09-19
There is no /USR. I assume you're talking about /usr. Capitalisation matters.

/usr must have permissions 755. With 774, normal users have no execute permission and cannot change to the directory or search its contents.

Try booting in recovery mode, then drop to a root shell. Remount the root partition in read-write mode and fix it. Or use a live disk.

---

