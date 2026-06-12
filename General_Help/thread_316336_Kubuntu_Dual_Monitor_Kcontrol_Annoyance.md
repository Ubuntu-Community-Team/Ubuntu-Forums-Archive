---
title: "Kubuntu Dual Monitor Kcontrol Annoyance"
date: 2006-12-10
forum: General Help
---

### Post by scpike on 2006-12-10
I'm getting annoyed with KDE.  I have a good handmade xorg.conf file which gives me direct rendering and 3d acceleration with two screens.  Everything was working fine until I decided to check out the KControl Monitor app.  Now, I get good working dual screens up through kdm, but as soon as I log in it switches to clone mode.  I don't know how to fix this, since the xorg.conf seems to have no effect on what KDE does with my screens after I log in.  If I set up dual screens through KControl I lose direct rendering, so I really want a way to have this module stop messing with things at all.

---

### Post by jayashleysmith on 2008-04-26
You could try uninstalling kcontroll, i had the same problem with another piece of software. But all i done was uninstalled it and works fine now.
sudo apt-get remove #package-name

Let me know how you get on!
Jay

---

