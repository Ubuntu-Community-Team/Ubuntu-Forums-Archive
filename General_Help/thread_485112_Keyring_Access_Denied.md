---
title: "Keyring Access Denied"
date: 2007-06-26
forum: General Help
---

### Post by MusicMastaMike on 2007-06-26
Hey guys, I've got a bit of an issue here. Every time I start up my laptop (Dell Inspiron E1505), it asks me for my password so nm-applet can access the keyring and log on to my network.  It will not accept my password, though, so therefore I can't get on the internet (although it will connect find to an unsecured network).  My password seems to work for everything else, except the keyring.  I have tried changing the root password as well, but no luck.  I've reinstalled the keyring and all its libraries, but that didn't work either.  Any ideas?

---

### Post by aJayRoo on 2007-06-26
The keyring password is not necessarily the same as either your/root password. Network manager uses the keyring to store all its passwords and it is likely that the first time you connected to a protected network you were also asked to provide a password for the default keyring (if this was the first time you had used the keyring). 

Unfortunately I no longer use wireless on my machine, hence no keyrings to check this out with, but I would suggest having a good look at the keyring manager (found in the system -> administration menu) as it may be possible to change the password for the keyring to something you know. As I said before this is really only a guess, but hopefully you will find something that helps you.

---

### Post by letkemanp on 2007-06-26
This may help

[http://ubuntuforums.org/showthread.php?t=463639&highlight=.gnome2%2Fkeyrings](http://ubuntuforums.org/showthread.php?t=463639&highlight=.gnome2%2Fkeyrings)

It is possible to remove/delete your keyring file, I think it's in the "/home/[username]/.gnome2/keyrings" folder called something like default.keyring. Before deleting the file I'd rename/move it somewhere else. By default if your system can't find the keyring file it will create it the first time its needed

If you search the forums for gnome2/keyrings then you may find other useful info.

---

