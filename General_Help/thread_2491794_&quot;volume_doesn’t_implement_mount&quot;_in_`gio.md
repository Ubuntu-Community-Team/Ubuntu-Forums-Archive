---
title: "&quot;volume doesn’t implement mount&quot; in `gio mount`"
date: 2023-10-20
forum: General Help
---

### Post by ittayd on 2023-10-20
In Ubuntu 22.04, when I do `gio mount google-drive://<my email>` I get "volume doesn’t implement mount". 
I used the Online Accounts Settings dialog to log into my account, I have gvfs, gvfs-fuse, gfvs-backends and ran the daemon, I tried to use dbus-run-session.

In my other laptop, a 20.04, the mount works fine. Not sure where the difference lies.

---

### Post by ittayd on 2023-10-26
Turned out this is because my terminal is a Flatpak package and Flatpak sets GIO_USE_VFS=local which is passed to the terminal and to my shell. Unsetting the value in my .zshrc fixed the issue.

---

