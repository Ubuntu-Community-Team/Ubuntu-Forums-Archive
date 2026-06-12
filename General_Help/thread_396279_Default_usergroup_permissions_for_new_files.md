---
title: "Default user/group permissions for new files?"
date: 2007-03-29
forum: General Help
---

### Post by likwid on 2007-03-29
Hi

How can i force that all new files are written with owner and group read write access and users read only? I find that i can umask 113, but it seems this only changes the command line and not gnome. I wish this to be default for the purpose of samba file sharing.

Thanks in advance!

---

### Post by fanatik on 2007-03-29
look in /etc/profile, you can set the umask in there, or preferably in your ~/.bash_profile, but you will have to log out of gnome and log in again for this to take effect.

Also you can look at **man smb.conf** for details on the masks you can apply in samba.

---

### Post by likwid on 2007-04-03
Hi

Thanks for help and sorry for delay getting back to you.

I'm afraid this works for terminal but not using nautilus. Any further ideas??

---

