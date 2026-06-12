---
title: "Disable, remove, or delete virtual terminals in Feisty"
date: 2007-05-04
forum: General Help
---

### Post by FakeOutdoorsman on 2007-05-04
I'm customizing a command-line (or sometimes called server install) installation of Ubuntu Feisty 7.04 for an old Panasonic CF-71 Toughbook with 128 MB of ram.  I'm trying to free memory by disabling most of the vitrual terminals.  This was easy to do in older Ubuntu installations because all you had to do was comment out the reference to each vitrual terminal in /etc/inittab.  Feisty is now using upstart and has no inittab file.  How should I disable the virtual terminals when there is no inittab file?

---

### Post by FakeOutdoorsman on 2007-05-04
I think I figured it out.  I just removed the tty files listed in /etc/event.d/.  Seems to have worked, but if I switch to TTY4 or above (alt + f4) then it just goes to a blank screen with a blinking cursor.  I can switch back though.

---

