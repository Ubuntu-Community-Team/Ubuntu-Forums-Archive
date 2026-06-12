---
title: "How to remove the disk icon from the desktop? [Resolved]"
date: 2006-11-19
forum: General Help
---

### Post by chinese_ys on 2006-11-19
I added one line in /etc/fstab to mount a fat32 partition automatically when the system boot up. But I do not like the icon of this partition on the desktop, may be it is really convenient.

so I want to remove the icon, but how can I do that? I am using Ubuntu 6.10.

thanks!

---

### Post by dcstar on 2006-11-20
> **chinese_ys said:**
> I added one line in /etc/fstab to mount a fat32 partition automatically when the system boot up. But I do not like the icon of this partition on the desktop, may be it is really convenient.

so I want to remove the icon, but how can I do that? I am using Ubuntu 6.10.

thanks!

System-Preferences-Menu Layout-System tools, add in "Configuration Editor"
then
Application-System Tools-Configuration Editor-Apps-Nautilus-Desktop and untick "volumes_visible".

---

### Post by chinese_ys on 2006-11-20
Thanks man!

---

