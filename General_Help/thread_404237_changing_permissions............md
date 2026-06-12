---
title: "changing permissions..........."
date: 2007-04-08
forum: General Help
---

### Post by jeetmcp on 2007-04-08
hi,
when i'm trying to extract .tar file to the icons folder, my system says that you don't have permissions to do this action. And when i'm manually changing permissions by doing right click on the /usr folder, it says that you can not change permissions of the /usr directory. is there anyway i can change permissions so that i can use .tar files and enjoy different icons on my system. the error message appears as mentioned below-
the permission could not be changed.i'm attatching screen shot of error message.

---

### Post by dreadlord_chris on 2007-04-08
> **jeetmcp said:**
> hi,
when i'm trying to extract .tar file to the icons folder, my system says that you don't have permissions to do this action. And when i'm manually changing permissions by doing right click on the /usr folder, it says that you can not change permissions of the /usr directory. is there anyway i can change permissions so that i can use .tar files and enjoy different icons on my system. the error message appears as mentioned below-
the permission could not be changed.i'm attatching screen shot of error message.

You do not want to go changing the permissions on your filesystem willy-nilly - that's a good way to completely screw it up.

To work with filesystem objects that your account doesn't have permissions for,  use **sudo** or the graphical equivs **gksudo** & **kdesu**
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2007-04-08
This should help:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

By the way, if you're trying to install an icon theme, you don't need to un-tar anything. Just go to System > Preferences > Themes and drop and drop the .tar.gz file into the Theme Manager window.

---

