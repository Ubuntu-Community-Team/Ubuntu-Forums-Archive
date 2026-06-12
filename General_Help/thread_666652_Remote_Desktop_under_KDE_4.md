---
title: "Remote Desktop under KDE 4"
date: 2008-01-13
forum: General Help
---

### Post by sjmacko on 2008-01-13
Remote desktop works fine when I log in under Gnome... No issues. I recently installed KDE 4 to take a look, and I am unable to control the Ubuntu machine from Apple Remote Desktop. It says that the connection was refused. If I log out of KDE and back into Gnome, it works fine. When I was in KDE, I checked the remote settings, and they were still intact.

My network settings all come up the same in KDE.... I can SSH into the machine, apache is still serving away, mysql is fine, but no remote desktop.


Any ideas?

Steve

---

### Post by sjmacko on 2008-01-14
Fixed... The krfb package was not starting up for some reason. I'm not that handy, so I decided to reinstall. I had to use the "force" option, but then everything worked... The screen quality is not as good as under gnome, but it works...

Steve

---

