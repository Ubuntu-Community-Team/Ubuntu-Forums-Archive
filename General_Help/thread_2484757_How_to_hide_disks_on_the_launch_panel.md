---
title: "How to hide disks on the launch panel?"
date: 2023-03-09
forum: General Help
---

### Post by stevermann on 2023-03-09
I have a dual boot system, Not in the traditional method, but by selecting the boot device on startup.  My default boot device has Ubuntu and the other drive has HAOS, but that is germane to the issue.

When I am in Ubuntu, which is most of the time, the HAOS volumes show on the launcher sidebar.  How can I hide those?


[IMG]https://ibb.co/8dGMmyd[/IMG]

---

### Post by MAFoElffen on 2023-03-09
Those are the Mounted Drives. To remove them from appearing in the Dock, then from a terminal, do:
```

gsettings set org.gnome.shell.extensions.dash-to-dock show-mounts false

```

---

### Post by maglin2 on 2023-03-09
GUI
Settings/Appearance/Configure dock behaviour/Show Volumes and Devices slider

---

### Post by stevermann on 2023-03-09
Many thanks. Both solutions are exactly what I wanted.

---

