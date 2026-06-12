---
title: "USB PMP HDD mount problem"
date: 2007-06-14
forum: General Help
---

### Post by wie6Ein0 on 2007-06-14
I'm having a problem with my RCA LYRA RD2780 portable media player. I connected it to my computer via USB and Ubuntu automatically recognized it and mounted it, adding an icon to the desktop. Everything seemed to be working fine until I noticed that it was read-only. I attempted to fix the problem, making the device allow the creation and deletion of files from it's 20GB HDD, but I instead rendered it useless. Now, when I connect it, I receive the error "Cannot Mount Volume. Unable to mount the volume 'AV_LYRA'. mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)"

The problem began after I right clicked on the desktop icon, went to properties, and tried to change the fmask to 777. All I want is to be able to get back to the settings and remove my custom details so that it will work again. At the moment, I cannot access the drive.

Please, tell me how I can access the drive again!

dmesg: [http://paste.ubuntu-nl.org/25526/](http://paste.ubuntu-nl.org/25526/)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=35344&stc=1&d=1181822201[/IMG]

---

### Post by smoker on 2007-06-14
what format is your drive? if ntfs try installing these:
install ntfs-3g and ntfs-config

---

