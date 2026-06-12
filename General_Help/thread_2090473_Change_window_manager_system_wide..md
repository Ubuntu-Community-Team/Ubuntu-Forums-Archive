---
title: "Change window manager system wide."
date: 2012-12-02
forum: General Help
---

### Post by SteveDeFacto on 2012-12-02
I've tried modifying several files to change the default window manager in xfce but nothing works. The only way is to save the session but this causes other problems such as start up applications being loaded more than once and chrome giving an error for some reason. It also seems to slow down the system start up but I could be just imagining it. Despite those problems I wanted to change the window manager across all users and future users.

---

### Post by dino99 on 2012-12-02
there is always dependencies issues when doing such move. You should not tweak the installation, and only install a new windows-manager; or better choosing something else than xfce if you dont like it.

---

### Post by Toz on 2012-12-02
> **SteveDeFacto said:**
> I've tried modifying several files to change the default window manager in xfce but nothing works.
Which files did you modify?
> The only way is to save the session but this causes other problems such as start up applications being loaded more than once and chrome giving an error for some reason. It also seems to slow down the system start up but I could be just imagining it.
> Despite those problems I wanted to change the window manager across all users and future users.
_For future users_, if you are running xubuntu or have installed xubuntu-default-settings in ubuntu, the file to edit is located at **/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-prechannel-xml/xfwm4.xml**. The property you want to change is the "theme" property (note that this will only change the window manager theme as you have stated above, not the appearance theme - in Xfce, there is a difference between the two. See:[http://ubuntuforums.org/showpost.php?p=12038130&postcount=4]("http://ubuntuforums.org/showpost.php?p=12038130&postcount=4")). In Xfce in ubuntu, I believe the file is located at **/etc/xdg/xfce4/xfconf/xfce-prechannel-xml/xfwm4.xml**. Making a change to one of these file will ensure that future users will get the window manager that you specified on first login. 

_For existing users_, you will need to modify the **$HOME/.config/xfce4/xfconf/xfce-perchannel-xml/xfwm.xml** for each user individually. You should probably do this when the user is not logged in, as the file will be overwritten on the user's logout with the window manager theme that is currently in use.

Keep in mind that the end user will still be able to change this setting through the Settings Manager at will.

---

