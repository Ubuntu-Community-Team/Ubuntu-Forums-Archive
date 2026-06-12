---
title: "Gnome crash-loop"
date: 2006-12-11
forum: General Help
---

### Post by Milesowl on 2006-12-11
I somehow managed to send my ubuntu installation into a never-ending crash-loop.

All I did was raising gnome top panel width to 100 pixel (where the icons get big etc..) then the system froze and flushed me back to the login screen... now everytime I log in.. the system does the same... or a black screen for a couple of seconds before sending me back again at login screen.

Anyone has a clue ? Should I fill in a bug report ?

---

### Post by hikaricore on 2006-12-11
I had this happen to me once, it seems to be a bug in gnome, the only way I found around it was to basicly reset gnome by removing (or moving) the configuration files in my home directory.

Hit: ctrl+alt+F1 to get to a terminal screen.

Then login you should be at your ~ aka home directory.

> 
mv .gconf .gconf-bakup
mv .gconfd .gconfd-backup
mv .gnome .gnome-backup
mv .gnome2 .gnome2-backup

Should basicly keep all your config files where gnome can't find them.  It will then rebuild them.

type: *logout*


then hit: ctrl+alt+F7

This will take you back to GDM where you should now safely be able to login.

---

### Post by hikaricore on 2006-12-11
There are config files in the .gconf (or .gconfd i can't remember which) directory which control the layour of your gnome-panel bars, so once you're back to your desktop, you can try and locate these files so if you want to restore your previous layout, you'll be able to.  :)

This is why we didn't delete these files.  However if you're just happy logging in again, and don't care about recustomizing, this should work perfectly.

---

### Post by Milesowl on 2006-12-11
Thanks man, it all worked easily !  You saved my desktop lol

---

### Post by hikaricore on 2006-12-11
Np, just glad someone else didn't have to go through the hairpulling I did over the exact same issue lol.

---

### Post by Sebastral on 2006-12-12
Had the same loop problem after an apt-get upgrade and hikaricore saved my day :)

---

### Post by Sebastral on 2006-12-13
Well, not entierly. It keeps crashing if I modify the gnome panel too much :(. Guess I'll move to enlightenment a little sooner :)

---

### Post by ububaba on 2007-01-13
> **hikaricore said:**
> I had this happen to me once, it seems to be a bug in gnome, the only way I found around it was to basicly reset gnome by removing (or moving) the configuration files in my home directory.

Hit: ctrl+alt+F1 to get to a terminal screen.

Then login you should be at your ~ aka home directory.



Should basicly keep all your config files where gnome can't find them.  It will then rebuild them.

type: *logout*


then hit: ctrl+alt+F7

This will take you back to GDM where you should now safely be able to login.

I am facing a similar problem. You say that one should[COLOR="Red"] Hit: ctrl+alt+F1 
to get to a terminal screen.[/COLOR] Silly as it may sound,**** my quandry is, when to hit?:-?

---

### Post by Krymzon on 2007-01-14
e.g. when gdm has loaded, but before logging in - that is at the moment you are supposed to enter your username in GUI

---

### Post by ububaba on 2007-01-14
> **Krymzon said:**
> e.g. when gdm has loaded, but before logging in - that is at the moment you are supposed to enter your username in GUI

Thanks for the hint, it resulted in this flag:
[HTML]
GDM could not write your authorisation file. This could mean that you are out of disk space 
or that your home directory could not be opened for writing. In any case, it is not possible
to log in. Please contact your system administrator.[/HTML]

It is very likely to be true that I have run out of disk space. I am the only user, I will be
needing you guys help. The situation can't be that impossible as it sounds.:confused:

---

### Post by Krymzon on 2007-01-15
I guess it should be possible to delete some files using a live CD, e.g. the standard Ubuntu installation disk. Or you can learn the basics of textmode, which really isn't that hard, and remove something using the rm command&#8230;

---

