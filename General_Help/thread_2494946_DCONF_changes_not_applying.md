---
title: "DCONF changes not applying"
date: 2024-02-01
forum: General Help
---

### Post by Jamesy281 on 2024-02-01
I am running a vanilla Ubuntu 22.04 PC. I followed the directions from [here]("https://help.gnome.org/admin//system-admin-guide/3.12/screen-locking.html.en") to configure global screen locking, however, when I run dconf update the settings are not applied.


I have tried logging out and also restarting, but the settings remain the same.


Is there another dependency or step I might have missed?

---

### Post by Dennis N on 2024-02-01
The URL you give is for Gnome 3.12 which was a long time ago. Ubuntu 22.04 uses Gnome 42.  - the guide stops at Gnome version 3.38. 3.38 was followed by Gnome versions 40 to 45. So the directions might no longer work.

Here is the index of versions covered by that guide:
[Gnome System Admin. Guide]("https://help.gnome.org/admin/system-admin-guide/")

Things that could be changed in 3.12 possibly can no longer be changed by the user, but still be in dconf-editor. Reducing the ability of the user to configure the system seems to be a trend with Gnome.

---

