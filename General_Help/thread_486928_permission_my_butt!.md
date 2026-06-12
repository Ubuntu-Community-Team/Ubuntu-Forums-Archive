---
title: "permission my butt!"
date: 2007-06-28
forum: General Help
---

### Post by nate22 on 2007-06-28
so ive loaded and corectly installed a apache 2.0 deamon 
meaning that i can correctly view the standard website it comes with.

but when ever i trry to edit that index.html file it keeps saying i dont have permission..any way to fix?

---

### Post by Ayuthia on 2007-06-28
You will need to use gksu gedit /var/www/index.html in order to get access to the file.

---

### Post by nate22 on 2007-06-28
i get this


nate@Nate:~$ gksu gedit /var/www/index.html
GTK Accessibility Module initialized

(gedit:19352): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
ALSA lib pcm_dmix.c:819:(snd_pcm_dmix_open) unable to open slave
nate@Nate:~$

---

