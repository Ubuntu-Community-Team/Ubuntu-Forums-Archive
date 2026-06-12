---
title: "How to require password on login using command line on ubuntu 12.04?"
date: 2013-12-29
forum: General Help
---

### Post by dannyw161 on 2013-12-29
I use gnome so I dont have all the menus people write about.

How do I require a password on login using the command line on ubuntu 12.04?

---

### Post by dannyw161 on 2013-12-29
I already tried the following with no success.

Run the following command in terminal:

  sudo gpasswd -d username nopasswdlogin
  substitute your username for username.

---

### Post by steeldriver on 2013-12-29
Are you using gdm or just a gnome desktop session under lightdm? I am only familiar with lightdm, but there are 2 distinct modes that people often confuse

1. **passwordless login**: the system boots to a GUI login screen, the user must choose (or enter) their login name but after that they are logged on without supplying a password. This is the behavior that is controlled by membership of the nopasswdlogin group.

2. **autologin**: a single named user is logged in to their desktop session automatically, bypassing the GUI login screen altogether. In lightdm this is controlled by the autologin-user=*username *setting in the [Seat Defaults] section of /etc/lightdm/lightdm.conf and can be set up either by editing that file directly or by running

```
sudo /usr/lib/lightdm/lightdm-set-defaults --autologin *username*
```

AFAIK there isn't a specific command to remove an autologin user using lightdm-set-defaults (although iirc setting an empty "autologin-user=" does work, I wouldn't recommend it) so you need to edit the file. From the command line you can do that with nano / vi / vim etc or with sed e.g.

```
sudo sed -i '/autologin-user/d' /etc/lightdm/lightdm.conf
```

---

### Post by dannyw161 on 2013-12-30
Thanks, it worked.

---

