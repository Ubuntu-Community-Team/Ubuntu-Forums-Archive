---
title: "Cursor Invisible after installing updates to 15.10"
date: 2015-11-23
forum: General Help
---

### Post by streak3 on 2015-11-23
Howdy Folks..
I installed 15.10 and recently installed recommended updates.  After updates installed, I no longer have a cursor.  I have tried the recommendations in [http://askubuntu.com/questions/62607...r-15-04-update]("http://askubuntu.com/questions/626078/mouse-cursor-invisible-after-15-04-update") and no success... Any help appreciated!!

---

### Post by streak3 on 2015-11-23
Getting closer.. have cursor now... but touchpoint not moving it :)

Open a terminal (Ctrl+Alt+T) and use the following command
 "gsettings set org.gnome.settings-daemon.plugins.cursor active false"

---

### Post by streak3 on 2015-11-23
Had to go into Advance BIOS settings and enable internal pointing device... all working now..

---

