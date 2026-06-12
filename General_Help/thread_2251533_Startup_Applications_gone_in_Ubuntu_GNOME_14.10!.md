---
title: "Startup Applications gone in Ubuntu GNOME 14.10?!"
date: 2014-11-04
forum: General Help
---

### Post by The Bright Side on 2014-11-04
Hey everybody, I installed Ubuntu GNOME 14.10 and then used the GNOME PPAs to update to GNOME Shell 3.14. Now the Startup Applications app is gone. Has anybody else experienced this and found a solution?

EDIT: I know the Tweak Tool has a "Startup Applications" section, but that section seems broken. When I click on the "+" button, nothing happens. Also, only 3 applications are displayed when there should be easily more than a dozen.

---

### Post by munjunga on 2014-11-05
> **The Bright Side said:**
> Hey everybody, I installed Ubuntu GNOME 14.10 and then used the GNOME PPAs to update to GNOME Shell 3.14. Now the Startup Applications app is gone. Has anybody else experienced this and found a solution?

EDIT: I know the Tweak Tool has a "Startup Applications" section, but that section seems broken. When I click on the "+" button, nothing happens. Also, only 3 applications are displayed when there should be easily more than a dozen.


I am using unity and facing the same problem. I want to enable numlock on logon and mute sound. I used startup in 14.04. 14.10 fails as I have no access to startup application

---

### Post by rbmorse on 2014-11-05
Drop a .desktop launcher file pointing to the executable into:

~/.config/autostart

Might be easier to symlink the desired application's launcher from /usr/share/applications, but I haven't tried that.

EDIT:  just tried the symlink idea. It works.

---

