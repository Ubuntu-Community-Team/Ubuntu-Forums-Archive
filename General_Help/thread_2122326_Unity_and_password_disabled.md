---
title: "Unity and password disabled"
date: 2013-03-04
forum: General Help
---

### Post by pofadda on 2013-03-04
I've lost the Unity desktop, seeing only the wallpaper covered with grid dots and a login box to the left and my password is not recognised.

This happened after trying to install Nvidia's own driver which seems to need the Nouveau driver to be disabled.  It wrote a *disable*.conf file to /etc/modprobe.d/ to do this and seems to have knocked out the 12.10 UI.  I eventually discovered Ctrl-Alt-T to bring up the terminal and deleted the said .conf.  They must have disabled some other files, too.

As I said, my password is seemingly wrecked too.

Login at CLI works fine but not at the above UI.  
Tried various options in [http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values](http://askubuntu.com/questions/70572/reset-unity-and-gnome-to-default-values) with no success: 
renamed dconf and compiz-1. 
ran gconftool-2 --recursive-unset /apps/compiz-1 
unity --reset &
and
rm -rf .gnome .gnome2 .gconf .gcond .metacity

Any idea what best to do now, or can I replace the UI and get my password back by some repair/reinstall action, please?

---

