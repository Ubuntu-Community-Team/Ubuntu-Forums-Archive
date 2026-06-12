---
title: "LTSP Ubuntu 7.10 Client umask settings"
date: 2008-02-29
forum: General Help
---

### Post by keenboy on 2008-02-29
I'm trying to change the umask settings for my LTSP Clients. I want to change it so that files and folders have the permissions of chmod=770.

I have successfully achieved this for a local user by editing /etc/profile but it doesn't work from a thin client instead it creates files and folders with the following permissions rwx-r-xr-x which makes it difficult when trying to implement shared folders etc.

I have also edited /opt/ltsp/i386/etc/profile in the same way and updated the ltsp-image but still no joy.

Does anybody know where I can change the umask for my LTSP clients?

Thanks

---

### Post by keenboy on 2008-02-29
The way I solved his was to edit

/etc/X11/Xsession.d/55gnome-session_gnomerc

and add

umask 0007

to the end of the file

---

