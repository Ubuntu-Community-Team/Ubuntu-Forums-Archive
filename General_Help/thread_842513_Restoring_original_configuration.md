---
title: "Restoring original configuration"
date: 2008-06-27
forum: General Help
---

### Post by Pabx on 2008-06-27
how can i restore original configuration on xubuntu? can it be done?

---

### Post by Elfy on 2008-06-27
Think the only way would be to reinstall it I'm afraid.

---

### Post by x1a4 on 2008-06-27
Hi,

Delete the ~/.config/ directory and the various dot files/directories in your home directory.  If you only want to reset Xfce settings, delete ~/.config/xfce4/ , ~/.config/xfce4-session/ , ~/.config/xfce4-taskmanager.rc

For Mousepad and Xfmedia it's ~/.config/mousepad/ and ~/.config/xfmedia respectively.  Just look in your home direcotry and in ~/.config/ for configuration files. 

To reset various applications run
```
sudo dpkg-reconfigure *package_name*
```
Where *package_name* is the name of the package you want to reset to default values.

EDIT: You can also reboot into Recovery Mode and you'll have a menu with a variety of options allowing you to do various things, like reconfigure your X server to default values.

---

