---
title: "Something odd... I think my GNOME desktop is running"
date: 2007-10-13
forum: General Help
---

### Post by Henaro on 2007-10-13
Hello everyone~

I just installed AWN and for some odd reason now when I use the cube, I can see my GNOME desktop behind my KDE desktop.  This includes the wall paper and icons that are on it.  

Tthe only GNOME app running right now is Firefox.  

Anyone know what's going on?  :confused:

---

### Post by mpgarate on 2007-10-13
thats strange... does it look cool?

---

### Post by Henaro on 2007-10-13
> **mpgarate said:**
> thats strange... does it look cool?

Actually... yeah.  I have a communist themed Gnome desktop.  And my KDE one is blue... Heehee


EDIT:I tried logging in and then out but it's still there.  :(

---

### Post by ddrichardson on 2007-10-13
If Gnome is definately not running (i.e. ps -e lists nothing) then I'd imagine its down to the cube not being redrawn properly.

Might be worth filing as a bug. Have you rebooted since this occured?

---

### Post by Henaro on 2007-10-13
> **ddrichardson said:**
> If Gnome is definately not running (i.e. ps -e lists nothing) then I'd imagine its down to the cube not being redrawn properly.

Might be worth filing as a bug. Have you rebooted since this occured?

This is what I got:

> $ ps -e | grep gnome
31457 ?        00:00:00 gnome-vfs-daemo


I havn't rebooted, but I have logged off the session.  I'll probably reboot later today though.

---

### Post by Henaro on 2007-10-13
I just rebooted.   And it's still there.  Anyone know how to solve this?  I think it's eating my ram.  Right now I'm using up 500 MBs of RAM and I only have Firefox and konsole open (along with XGL and compiz).  It's usually at 350 MBs.  :(

---

