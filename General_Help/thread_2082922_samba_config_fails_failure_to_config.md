---
title: "samba config fails failure to config"
date: 2012-11-10
forum: General Help
---

### Post by sdowney717 on 2012-11-10
when following this procedure does not work
[http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/](http://www.liberiangeek.net/2012/03/filesharing-in-windows-7-and-ubuntu-12-04-precise-pangolin/)

so looking for another help maybe needs to run as root which also does not work.
[http://unix.stackexchange.com/questions/14288/easily-share-a-folder-with-a-windows-computer-in-fedora-15-gnome-3](http://unix.stackexchange.com/questions/14288/easily-share-a-folder-with-a-windows-computer-in-fedora-15-gnome-3)

shows the terminal picture failure
> scott@scott-P5QC:~$ gksu system-config-samba
invoke-rc.d: unknown initscript, /etc/init.d/samba not found.
scott@scott-P5QC:~$ gksu system-config-samba


all I want to do is share my files from ubuntu to windows 7.:(

---

### Post by cariboo on 2012-11-11
Precise doesn't have an /etc/init.d/samba. It now uses nmbd and smbd. The qui configuration tool needs to be updated. I'd suggest setting up /etc/samba/smb.conf manually.

---

