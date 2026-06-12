---
title: "Transfering files from Windows partition to Linux partition"
date: 2005-09-25
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-25
Is there an application that makes it possible to transfer files from a Windows partition to a  Linux one?
Thank you!

---

### Post by Leif on 2005-09-25
mount the windows drive as detailed here : [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows), then copy the files as you normally would

---

### Post by ubuntuubuntu on 2005-09-25
When I type "sudo mount -a", I get the followinf message:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What should I do?

---

### Post by Leif on 2005-09-25
did you mount it using the correct filesystem type ? fat32 vs ntfs ?

---

### Post by aysiu on 2005-09-25
[QUOTE=ubuntuubuntu]When I type "sudo mount -a", I get the followinf message:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What should I do?[/QUOTE] Please follow the instructions in the link Leif gave you. *sudo mount -a* remounts /etc/fstab without rebooting. That's not what Leif linked to.

---

