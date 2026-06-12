---
title: "GDM problem"
date: 2013-03-27
forum: General Help
---

### Post by uzumakifahim on 2013-03-27
I have installed GDM and successfully set as my default display manager. Now, I can't install any new theme for the GDM, it's only giving me a plain theme, but want to use another, how can I do that? When I am searching for GDM or login window in the dash it saying "nothing found".

How can I install a new theme for GDM. Please help anyone.

---

### Post by ManamiVixen on 2013-03-27
GDM isn't themeable anymore, period, on Gnome 3.6 and later. On Gnome 3.4 to 3.2, you'll have to replace the default gnome-shell theme with your shell theme in the /usr/share/gnome-shell/ folder. Just make sure the theme you will switch out has a GDM file in it or GDM will crash. Gnome 3.0 requires messing with the GTK theme for login.

---

### Post by CaptainMark on 2013-03-27
Perhaps consider installing MDM, which is themeable, its forked from the old GDM before Gnome3 came into place, your profile pic says you are using Ubuntu 12.04,[ this link will help]("http://www.webupd8.org/2012/11/how-to-install-latest-mdm-display.html") but if you just haven't updated your profile and you're using Ubuntu 12.10 then you can't install MDM and keep gnome-shell due to conflicts.

---

### Post by uzumakifahim on 2013-03-28
Thanks both of you for your reply. From this discussion I think, I want MDM, but if I want to use it on Ubuntu 12.10 with Gnome Shell, then my Gnome Shell will be removed. **But what about Unity? Will MDM affect Unity on Ubuntu 12.10 anyway?**

---

### Post by CaptainMark on 2013-03-28
It shouldn't no, Unity depends on lightdm not GDM and lightdm does not clash with MDM so you can have them installed side by side

---

### Post by uzumakifahim on 2013-03-28
Thanks to all, marking this post as solved.

---

