---
title: "missing glass folder icon"
date: 2008-04-26
forum: General Help
---

### Post by adohall on 2008-04-26
The glass folder icon (from Glass Icons) won't show in Hardy Heron for some reason. Any one know why that might be?

---

### Post by adohall on 2008-04-28
A couple fo very helpful Ubuntu users agave me the solution obver at gnome-look.org:

1. Open Nautilus with root permission (terminal - sudo nautilus)
2. Extract the Glass Icons tar.gz file into /usr/share/icons folder.
3. Go to /usr/share/icons/glass-icons/scalable/filesystems/ and right click the gnome-fs-directory.svg file and select the Make Link option. This will create a link and you rename that link folder.svg.
4. Do the same with these other files:
- gnome-fs-trash-full.svg -> user-trash-full.svg
- gnome-fs-trash-empty.svg  -> user-trash.svg
- gnome-fs-home.svg -> user-home.svg
- gnome-fs-client.svg -> computer.svg
- gnome-fs-web.svg -> applications-internet.svg
- gnome-fs-desktop.svg -> user-desktop.svg
- gnome-fs-server.svg -> network-workgroup.svg
- devices/gnome-dev-harddisk.svg -> drive-harddisk.svg
- devices/gnome-dev-dvdrw.svg -> drive-optical.svg
- devices/gnome-dev-removable.svg -> drive-removable-media.svg
5. Customize a theme by choosing Glass Icons;
6. Reboot (or change icon theme and then change back)

---

