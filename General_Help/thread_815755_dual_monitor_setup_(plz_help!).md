---
title: "dual monitor setup (plz help!)"
date: 2008-06-01
forum: General Help
---

### Post by Rainstride on 2008-06-01
im currently trying to setup 2 monitors to run as separate desktops. i use a ati radeon x1300 xge. i have no clue how to config the xorg file:confused:, so any help would be great :).

---

### Post by SirPerigrin on 2008-06-01
Ill ease your fears right now, you dont need the xorg file!!! This can be setup from a GUI!!!

Make sure you have the restricted ATI drivers installed then

> sudo apt-get update
sudo apt-get install fglrx-control

This installs Catalyst Control Center, which has a nice GUI for managing all your graphics card functions, including dual-monitors

---

### Post by Rainstride on 2008-06-02
iv tried that to, it usually ends up breaking my setup. that and theres no setting to change them to be independent of each other.just clone and big desktop.:icon_frown:

---

