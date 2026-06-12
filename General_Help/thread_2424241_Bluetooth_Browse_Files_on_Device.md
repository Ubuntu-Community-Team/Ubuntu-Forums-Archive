---
title: "Bluetooth: Browse Files on Device"
date: 2019-08-05
forum: General Help
---

### Post by makem2 on 2019-08-05
I have already installed blueman, bluez and their dependencies, with the addition of  obexftp and  libobexftp0.

Determine file manager:

```

makem@ssdTOSH:~$ xdg-mime query default inode/directory
exo-file-manager.desktop
makem@ssdTOSH:~$

```

In Bluetooth Local Services Transfer Settings:

Incoming Folder: Downloads
Checked Accept files from trusted devices
Advanced: exo-file-manager.desktop --browser obex://[%d]

Bluetooth Browse files on Device:

Select Galaxy S8:

Error: Flailed to launch "exo-file-manager.desktop"
Failed to execute child process "exo-file-manager.desktop" (No such file or directory)

```

makem@ssdTOSH:~$ exo-open --launch FileManager
makem@ssdTOSH:~$

```

Opens the file manger on the desktop correctly but when entered in  Bluetooth Local Services Transfer Settings it gives an error too.

Advanced: exo-open --launch FileManager --browser obex://[%d]

Error: Failed to execute default File Manager
Input/output error

Can anyone assist with the correct command to open the file manager and browse android phone files?

---

### Post by makem2 on 2019-08-08
My solution to date:

Install Solid Explorer from Google Play and browse Android files via FileZilla.

SD card is accessible too.

---

