---
title: "FTP Users Accessing Removable Media"
date: 2013-12-17
forum: General Help
---

### Post by greg.routenburg on 2013-12-17
I'm trying to setup an FTP server to share content on removable media with a program that will only interface with the rest of the server by FTP.  Specifically, I need to copy materials from hotswapable removable hard drives, USB drives and DVD-ROMs.  I can configure an FTP user in the system and set their home directory to the "/media" folder but when the media is inserted it mounts the subfolders with access only to the admin user account that's logged into the server at the time.  The FTP client can't navigate beyond the root of the media folder.  

Is there a way to automatically change the user permissions of the directories that are created when devices are automounted?   

I also need to know if the automount point can be changed from the /media folder to a different location.

I'm using Ubuntu 12.04.

Thanks for any possible insight.

---

