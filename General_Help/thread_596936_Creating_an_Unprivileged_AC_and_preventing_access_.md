---
title: "Creating an Unprivileged A/C and preventing access to WIn XP C: drive"
date: 2007-10-30
forum: General Help
---

### Post by rahimveron on 2007-10-30
I wanted to create an Unprivileged account for my little sister and want to give the following privilege like using audio, music, internet, games, etc.
Everything is fine. But i noticed that through her a/c she can access WIn XP C: drive by navigating to /media/sda1, which i want to keep away from her.
Another /media/sda5 has all music and videos which can be accessed by her, no problem here.

Just want to prevent her from accessing C: drive,ie, /media/sda5
Another thing while creating her a/c in which "group" should i put her? A new group like sister?

I have an another user named "gir" and home/gir folder. gir belongs to his own "gir" group.
I want gir and me(the ist a/c created during installation) can access and create & read both of our home folders, but dont want my Sister to access the two folders as i can see that that she can access the /home/gir, folder but not mine. Where i am going wrong?
I dont want her to access my and gir home folder and prevent her to accessing XP C: Drive in /media/sda1.
Plz help me.
I want her to get use to Ubuntu and use it more often than XP

---

### Post by rahimveron on 2007-10-30
bump......

---

### Post by Archmage on 2007-10-30
Make yourself owner of the mount-point for your Windows C and give in the fstab the 700 permission (only you can do anything, no one else can do anything there.)

---

