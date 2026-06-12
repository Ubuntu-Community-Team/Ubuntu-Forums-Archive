---
title: "Script to mount and unmount a NAS share"
date: 2013-08-06
forum: General Help
---

### Post by stephencweston on 2013-08-06
Dear all,

I have a truecrypt container file which I have residing in a shared folder on a NAS. Unfortunately truecrypt does not allow me to access the share unless it is locally mounted. I've tried accessing it by typing the line 'smb://192.168.1.121/<share name>/<truecrypt file>' into select file line, but it can't find the location.

What I would like to do is create a script (which I can hopefully create a launcher for) that will enable me to quickly mount the share with full read/write access. Similarly, I would also like a script to also unmount the share too. I do not want to have the NAS share automatically mounted on boot-up or login as I will not always have the NAS drive switched on.

Ideally, I would like the script to run without it having to ask for root privileges. But I can live with that if necessary.

Unfortunately I do not know the best way to achieve this. I have tried googling for info, but it seems confusing. For example should I be using the 'mount' command or 'udisk' or 'gnome-mount' and what should the command line look like (the share does require a username and password to access).

Any help will be much appreciated. I'm not a complete noob and I'm not fearful of the command line, but I do need things explained to me. If you need any more info, please do ask.

Stephen

---

