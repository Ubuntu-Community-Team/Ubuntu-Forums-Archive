---
title: "Mounting external harddrive in KDE (switching from GNOME)"
date: 2007-08-25
forum: General Help
---

### Post by stormie_abdul on 2007-08-25
I just moved to KDE desktop.

In GNOME, when I plug-in my USB external harddrive (ntfs), it is automatically mounted.

But in KDE, it does work like it works in GNOME. I take the following steps.

1) I create a folder in /media using sudo mkdir /media/NewFolder

2) I  mount using
sudo mount /dev/sdb1 /media/NewFolder

3) Then I device is mounted but I don't have permission to access it. the permissoins are (dr-x------)

4) I can only access it by using root access.

sudo ls -l /media/NewFolder

I don't agree with this solution. What is the solution to this problem in KDE? I want my ntfs external harddrive to be easily accessible in KDE.

I will appreciate any help in this direction.

---

### Post by jclmusic on 2007-08-26
open konqueror, then click media. then right click on the icon of the drive u want to mount and click mount.

---

