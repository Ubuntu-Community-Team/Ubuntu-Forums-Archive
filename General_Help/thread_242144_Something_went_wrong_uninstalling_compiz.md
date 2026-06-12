---
title: "Something went wrong uninstalling compiz"
date: 2006-08-23
forum: General Help
---

### Post by darklemming54 on 2006-08-23
After uninstalling compiz i rebooted and was given an error that my gnome icons couldnt be found.  so now everything but my applications have grey pieces of paper for icons, and whenever i start X, my theme controls wont change.


to install compiz i followed [this]("http://ubuntuforums.org/showthread.php?t=222034&highlight=xgl%2Fcompiz") and to uninstall compiz i did the following

edit  /etc/gdm/gdm.conf-custom back to normal
remove /usr/bin/startcompiz


sudo apt-get remove xserver-xgl compiz-gnome cgwd cgwd-themes

---

