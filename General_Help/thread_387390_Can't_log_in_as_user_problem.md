---
title: "Can't log in as user problem"
date: 2007-03-18
forum: General Help
---

### Post by Declan on 2007-03-18
Arrgh!
A few days back I noticed that the Edgy installation was getting a bit funny. In particular, I couldn't shift to console mode using CTRL+ALT+4 any more. Then, apparently, it went mad by itself (I wasn't there to witness this myself). So it was shutdown for bad behaviour (after 32 days of good behaviour).
Then the problem was that it wouldn't allow user logins. After entering username and password correctly, it would attempt to login, but then give up and return me to gdm. It wouldn't allow me to get the console only login either. The only way to get at the console was to boot up again in safe mode, which logged me in as root.

Right, says I. I'll take this opportunity to have a look at Linux Mint. I've just installed that. But, amazingly to me, the same problem is happening. I concluded that it must be something in the home folder (which I kept). 
So I go into safe mode (as root) and go through the home folder of the user I am deleting all kinds of configuration files. Semi-randomly, I admit. 
To no avail.
Still as root, I type startx, and off starts the gnome desktop, though without the menubar. But I go back out to console mode, login as the user and then try startx, and I get the following error message: 
xauth: creating new authority file /home/me/.serverauth.4112
X: user not authorized to run the X server, aborting.
xinit: Server error

Help?!

Thanks,

Declan

---

