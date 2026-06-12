---
title: "ifup eth0 when cable is connected?"
date: 2007-01-29
forum: General Help
---

### Post by W. Irving on 2007-01-29
Is there a way to achieve a similar functionality to that in Windows where it detects when an ethernet cable has been connected, and configure that particular network device (i.e. ifup eth0, and ifdown when connection is lost)?

Perhaps an app that works with xfce?

---

### Post by strabes on 2007-01-29
sudo apt-get install network-manager network-manager-gnome

I don't know any app that does this for XFCE4. Sorry.

---

### Post by W. Irving on 2007-01-30
Thanx! Seems to work, as far as I can see. Nm-applet works too, but it doesn't detect any networks at all. I don't need it anyway.

---

