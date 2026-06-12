---
title: "Can't select themes in Login Window"
date: 2006-10-03
forum: General Help
---

### Post by xXx 0wn3d xXx on 2006-10-03
Hello I installed a new theme on my Dapper install and now I cannot select a theme. I get the default gnome login without a theme. How can I fix this ? Thanks.

---

### Post by orb9220 on 2006-10-03
Logon themes are not gnome themes. Known as gdm or logon screen, goto system>adminstration>logon screen. You can change to different ones there or go to gnome-look.org and look into other LogOn screens.

When you are at the logon screen you are not running gnome yet so no theme.

---

### Post by Dinerty on 2006-10-03
```
sudo apt-get install gnome-splashscreen-manager
```

Not sure if this is excatly what but it allows you to change your splash logon if you lost it?

---

### Post by xXx 0wn3d xXx on 2006-10-03
I am running gnome. Here is an example of what I am talking about. Look in the style box "Plain Plain with Face browser themed" is the only option I have.

Edit: I have solved a problem with a complete reinstall of gdm. It displayed "Plain Plain with Face browser themed." It was very strange but I fixed it. Thanks.

---

