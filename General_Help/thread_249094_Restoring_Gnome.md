---
title: "Restoring Gnome?"
date: 2006-09-02
forum: General Help
---

### Post by mikesena on 2006-09-02
Hi,

I tried to install XGL, but it REALLY failed.  I can't log into my system anymore.  I need to restore gnome without x server, when i boot my computer, it says 'X Server' failed, something about graphics.  i don't want x server anymore, i just want to go back to BEFORe i installed it.  i think i had to edit the gdm.conf file.  how do I do this?  i can't paste the contents, because its on another computer.

i have the ubuntu cd, is there a way i can use that to 'override' the boot settings, without loosing all my configurations, programs etc?

i think it's jsut some file i have to edit, but i don't know how.  please tell me!  or, please tell me how to fix my current problem (x server complaining about graphics not being setup right)

edit:  the message is something like:
  GDM: cannot start x server *it gives a path* XGL
  command not found!

any ideas on how to remove it, or **better yet** install XGL properly?

---

### Post by mikesena on 2006-09-02
ive fixed my problem, i edited the file /etc/gdm/gdm.conf-custom (with difficulty) using vi and it booted up again.

---

