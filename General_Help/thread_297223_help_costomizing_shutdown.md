---
title: "help costomizing shutdown"
date: 2006-11-10
forum: General Help
---

### Post by Ocxic on 2006-11-10
I just found out that by using the "halt -h" command that the system puts the hard drives in standby mode before powering off.

this would be a great way to prolong drive life by not letting the drives spin down unpowered.

I would like to use this command (or the same effect by other means) to shutdown my system by default, is there a way to modify the shutdown scripts or procedures in order for this to happen??

 -Bennett

---

### Post by Ocxic on 2006-11-11
bump

---

### Post by kerry_s on 2006-11-11
You could create a launcher to use instead of the normal shutdown gui. I think you need to add a line to the sudoers file so you don't have to enter a passwd on shutdown.

sudo visudo

(Your Name) ALL = NOPASSWD: SHUTDOWN

Than just use your command in your launcher.->

sudo shutdown now -h

or for reboot

sudo shutdown now -f -r

---

### Post by kerry_s on 2006-11-12
I thought i'd add a pic now that it's working

---

### Post by syadnom on 2006-11-12
this is unneccessary.  you could make a startup/shutdown script that does nothing at startup and runs the halt command at shutdown.  just copy an exsisting startup script over and modify accordingly..  this way the standard shutdown system will work(shutdown -r now or the normal shutdown/restart/etc gui from gnome/kde/gdm/kdm)

---

### Post by Ocxic on 2006-11-13
as i have never done this befor, could you give me an example of where i might find sucha script?? i figure /etc/init.d/ but i don't want to meddle in thing i don't know about. thanks

---

### Post by kerry_s on 2006-11-15
The shutdown & reboot script's are in /sbin, but it's a "elf" file aka: compressed data. Not the easiest thing to mess with.

---

### Post by phoechan on 2007-09-20
> **Ocxic said:**
> I just found out that by using the "halt -h" command that the system puts the hard drives in standby mode before powering off.

this would be a great way to prolong drive life by not letting the drives spin down unpowered.

I would like to use this command (or the same effect by other means) to shutdown my system by default, is there a way to modify the shutdown scripts or procedures in order for this to happen??

 -Bennett

hihi

---

