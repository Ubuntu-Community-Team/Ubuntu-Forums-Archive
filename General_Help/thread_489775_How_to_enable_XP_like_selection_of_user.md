---
title: "How to enable XP like selection of user?"
date: 2007-07-01
forum: General Help
---

### Post by putkis on 2007-07-01
We have two user accounts in our home PC. When Xubuntu starts, we would like to get to a screen where you see names of both users and can choose your own account by clicking the name, without giving any passwords (not needed in our case). So is there a way to make xubuntu login behave like Windows XP?

---

### Post by Brucevdk on 2007-07-01
EDIT: I did this under GNOME/GDM, I'm don't know anything about XFCE but most of the stuff here is probably window manager independent though you'll have to update the location of the pam.d file.

I searched the forums and found a possible solution, I'm not making any guarantees that it's "The Right Way (TM)" but it will work just like you requested (user selection and no password). It is important to remember that using this method all users will still have a password but the login window just won't check for it.

First you'll have to select a proper login window, do this using *System -> Administration -> Login Window*. An example would be *Human List*, the one at the bottom.

Next create a text file */etc/X11/gdm/nopassusers* and add the usernames of the users you want to be able to login without asking for a password. The location and the name of this file don't matter, it's just some file to store some names in that's all. One user per line, i.e.
```

bruce
putkis

```

The last thing you'll have to do is open */etc/pam.d/gdm* in your favorite text editor using *gksudo gedit /etc/pam.d/gdm* for example. You'll have to add the following line inmediatly after *auth	required	pam_env.so*.
```

auth	sufficient	pam_listfile.so item=user sense=allow file=/etc/X11/gdm/nopassusers onerr=fail

```

What this does is allow the users whose name is found in the nopassusers file to login without entering their password. I haven't looked up how PAM works or how this file is processed so I'm not sure what else could be influenced by doing this.

For more details see [the original post]("http://ubuntuforums.org/showpost.php?p=66046&postcount=11").

---

