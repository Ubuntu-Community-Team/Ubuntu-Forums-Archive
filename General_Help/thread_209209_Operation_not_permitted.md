---
title: "Operation not permitted"
date: 2006-07-04
forum: General Help
---

### Post by hanzomon4 on 2006-07-04
I can't install gnome-control-center or gnome-panel I need help please. the ubuntu-desktop and everything with it is broken.. hence nothing works

```
E: /var/cache/apt/archives/gnome-control-center_1%3a2.14.2-0ubuntu1_i386.deb: unable to make backup link of `./usr/lib/libgnome-window-settings.so' before installing new version
E: /var/cache/apt/archives/gnome-panel_2.14.2-0ubuntu1_i386.deb: unable to make backup link of `./usr/share/man/man1/gnome-desktop-item-edit.1.gz' before installing new version


```

---

### Post by hanzomon4 on 2006-07-05
[-o< Please some one help I'am way in over my head. My system is on usable.. I don't have any thing, panels, menus, windows nothing. I can't even install kubuntu-desktop.. It downloads but its not added to the session menu. I tried to copy my media files and docs to another hard drive but it says "/folder/ omitted"

---

### Post by hanzomon4 on 2006-07-06
I fixed it, the problem was solved by using lsattr and fsck to check the disk... After the test was done and the system rebooted, the file was gone and I could finally install ubuntu-desktop. Here is the exact commands in case anyone else has the same problem.   


         Logout and press ctrl+alt+F1
         login and type ```
sudo telinit 1
```
         next type ```
mount -o remount,ro /
```
         and last ```
fsck /dev/* (path to where ever your root partition is)
```

---

