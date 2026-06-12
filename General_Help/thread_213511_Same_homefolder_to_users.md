---
title: "Same homefolder to users"
date: 2006-07-11
forum: General Help
---

### Post by macoute on 2006-07-11
I have 20 users in my system. They all need to share the same settings (and the altering of these settings in the future needs to be as easy as possible) . 
How do I set them using the same home directory? I have put them into the same group and set the permissions of this home directory by "chown -R user.group homedir", mounting the directory with nosuid. 
Users still can't login graphically because of the wrong permissions.

---

### Post by aysiu on 2006-07-11
When you say the same settings, are you talking about *all* settings or just the ones they notice?

If it's just the ones they notice, don't change ownership of anything, and don't change permissions on anything. Just put the settings in a separate folder and symlink them to each user's home folder.

For example, let's say they all use KDE, and you want them to have the same KDE settings. Create the settings you want in one user's account, then ```
rm -rf /home/seconduser/.kde
ln -s /home/firstuser/.kde /home/seconduser/.kde
```

---

### Post by macoute on 2006-07-17
I am using Gnome and I can't get these instructions working using it. I have symlinked directories .gconfd, .gconf, .gnome and (.metacity) but all the settings are not the same. If I symlink .gnome2 and/or .gnome2_private, gnome won't start at all, saying something about permission problem.

What are the directories I need to symlink?

---

### Post by aysiu on 2006-07-17
I would symlink for Gnome:

.gconf
.gconfd
.gnome
.gnome2
.metacity
.nautilus
.icons
.themes

---

### Post by macoute on 2006-07-18
I can't symlink .gnome2 for example, as it gives a error about permissions. 
```

Gnomen pikanäppäinkansion "/home/oppilas-30/.gnome2/accels" luonti epäonnistui: Permission denied

```
In english, it means that creating Gnome shortcut directory /home/oppilas-30/.gnome2/accels failed: Permission denied. I have chmodded this symlink to oppilas-30. How to fix?

---

### Post by aysiu on 2006-07-18
No idea.

---

### Post by jayemef on 2006-07-18
Look into the tools [Pessulus]("http://www.gnomefiles.org/app.php?soft_id=1082") and [Sabayon]("http://www.gnome.org/projects/sabayon/"), which are specifically designed to handle profiles for groups of users. These are advertised to be part of Gnome 2.14, so it's possible you already have them installed (can't verify this at the moment).

---

