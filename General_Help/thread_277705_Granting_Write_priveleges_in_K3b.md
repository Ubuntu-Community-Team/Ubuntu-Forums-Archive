---
title: "Granting Write priveleges in K3b"
date: 2006-10-15
forum: General Help
---

### Post by ramjet_1953 on 2006-10-15
Hi, Guys!

I have run into a problem when trying to copy an audio CD using K3b.
I am using an internal CD-RW/DVD drive to read and an external IEEE1395 LG Super Multi drive for recording.
K3b recognises the drives OK, but when it tries to write to the LG drive, it says that as a user, I don't have write priveleges.
When I go to the configure menu, I can see that this is so, but there doesn't seem to be any way to change it here.
There is probably one of those damned command line things that allows you to change write priveleges, but as a fairly recent Ubuntu convert, I have no idea how to do it.
Some help here would be appreciated.

Rgards,
Roger:(

---

### Post by peanut butter on 2006-10-15
I think you have to run K3b as root to write to cds. so something like kdesu k3b or in gnome gtksu k3b :)

---

### Post by ramjet_1953 on 2006-10-16
Don'tlike the idea of running K3b in root mode.
Surely there must be a way of granting write priveleges to users?

---

### Post by taurus on 2006-10-16
Try adding yourself to group cdrom in /etc/group!!!

---

### Post by ramjet_1953 on 2006-10-16
Thanks for the replys!

Had a look in /etc/group and my login is already in there for CD ROM's.
Where do I go from here?

Regards,
Roger

---

### Post by Zeddicus on 2006-10-17
Strange -- I know for a fact that I used to need to do that, but I no longer need root -- which version of KDE/K3b are you using?

---

