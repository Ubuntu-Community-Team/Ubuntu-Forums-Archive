---
title: "Long delay after login to desktop display"
date: 2022-02-07
forum: General Help
---

### Post by harry5552 on 2022-02-07
Using 21.10 fully up to date which was installed from scratch

When I login in there's a long delay before the desktop is shown, e.g syslog - 

Feb  7 08:32:24 ubuntu5 update-notifier.desktop[5295]: Cannot stat file /proc/4481/fd/75: Permission denied
Feb  7 08:32:24 ubuntu5 update-notifier.desktop[5295]: Cannot stat file /proc/4481/fd/76: Permission denied
Feb  7 08:32:24 ubuntu5 update-notifier.desktop[5295]: Cannot stat file /proc/4481/fd/1023: Permission denied
**Feb  7 08:33:22** ubuntu5 systemd[2957]: Started Application launched by gnome-session-binary.
**Feb  7 08:35:01 **ubuntu5 CRON[5314]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Feb  7 08:35:22 ubuntu5 systemd[2957]: app-gnome-org.gnome.DejaDup.Monitor-5300.scope: Deactivated successfully.
Feb  7 08:35:32 ubuntu5 anacron[1113]: Job `cron.daily' started

I have more of the logs if required but anyone any idea why there's nearly a 100 second wait between lines 4 & 5?

thanks in advance

---

### Post by TheFu on 2022-02-09
Check dmesg.

---

