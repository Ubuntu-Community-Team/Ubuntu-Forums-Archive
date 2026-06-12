---
title: "Unable to uninstall package"
date: 2016-01-12
forum: General Help
---

### Post by florian.kapteina on 2016-01-12
I recently installed an application (UnityLauncherFolders), but now I'd like to uninstall it. 
The Problem is that the Package installed from a .deb file is not shown in the SoftwareCenter, further I'm not able to delete it manually in the /usr folder.

---

### Post by howefield on 2016-01-12
Try this from the terminal.. (assuming the package name is unity-launcher-folders)

```
sudo apt-get purge unity-launcher-folders
```

eg.
```
hugh@xenial-laptop:~$ sudo apt-get purge unity-launcher-folders 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  unity-launcher-folders*
0 to upgrade, 0 to newly install, 1 to remove and 0 not to upgrade.
After this operation, 259 kB disk space will be freed.
Do you want to continue? [Y/n] 
(Reading database ... 202905 files and directories currently installed.)
Removing unity-launcher-folders (14.09.4) ...
Processing triggers for libglib2.0-0:amd64 (2.47.3-3) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.2~bzr0+16.04.20151217-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.59ubuntu1) ...
hugh@xenial-laptop:~$ 
```

---

