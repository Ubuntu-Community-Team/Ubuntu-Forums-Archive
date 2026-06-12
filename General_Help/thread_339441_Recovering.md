---
title: "Recovering"
date: 2007-01-15
forum: General Help
---

### Post by Bider on 2007-01-15
Whenever i start ubuntu & login, it begins to start but that fails and tells me that a 'drmc' file is missing. And it boots me back to the login screen.

I also noticed my /home/* folder was missing and all my installations.
Im not sure what caused this, as i have been away from the computer for about a week.

I tried recovery mode, but still no luck. any clues on recovering or repairing the installation of ubuntu?.

---

### Post by Seadap on 2007-01-15
It's a file that contains some of your default session settings and it's located in your home directory.  If that directory is gone, so is the file...

---

### Post by aysiu on 2007-01-15
I don't know what happened to your /home/* folder, but you can create a new user and use that user to log in graphically and investigate.

Boot into recovery mode and type ```
adduser *username*
adduser *username* admin
reboot
``` where *username* is a different username from the one you used earlier. Then, when you get to the Ubuntu login screen, log in with that user.

---

