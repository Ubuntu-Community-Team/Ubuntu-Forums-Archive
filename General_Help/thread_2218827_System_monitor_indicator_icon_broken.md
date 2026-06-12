---
title: "System monitor indicator icon broken"
date: 2014-04-22
forum: General Help
---

### Post by Wayne Twine on 2014-04-22
HI 

After upgrading to 14.04, the system monitor indicator icon in Unity panel has been replaced with a crossed out red circle.  I tried editing the indicator_sysmonitor.desktop file in /usr/share/applications by setting the icon path to an existing icon (and then saving and rebooting), but that only changes the icon of the app in Unity dash, but no in the panel itself.

Where do you set the icon for the app indicator in the panel?

W

---

### Post by ami7878 on 2014-08-12
I have the same problem after upgrading to 14.04.1

**Update:** I found the issue is due to that the indicator is using an icon name sysmonitor and that cannot be found. I solved this (on my machine) by adding an icon, named sysmonitor.png, to /usr/share/icons/my_icons_of_choice/status/24 folder.

---

