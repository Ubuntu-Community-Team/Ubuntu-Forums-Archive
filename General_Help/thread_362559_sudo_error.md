---
title: "sudo error"
date: 2007-02-15
forum: General Help
---

### Post by zraffz on 2007-02-15
When I go to login using sudo, it says invalid/incorrect password... this would be my login name's password, correct? Also I don't believe I set a su password, can anybody assist me on why this is happening? I have tried using my login password for both sudo and su; neither worked..

---

### Post by rsambuca on 2007-02-15
By default, ubuntu does not allow you to log-in as root user, as a good-practices and safety measure.  Is there a reason you wish to do so?

---

### Post by n00bish on 2007-02-15
"su" makes you root - Ubuntu does not come with a root password enabled, hence nobody can log in as root, or su to root.  You can get around that by typing "sudo su" and then your username's password, though this is really not recommended unless you know what you are doing.

For the sudo problem, would you have happened to add a second account to your machine other than the main one?  Other than that, make sure for the usual things - shift isn't being pressed by accident, caps lock is off, etc, and try again.

Let me know if any of that helps.

---

### Post by Maestro23 on 2007-02-15
Just FYI: RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by zraffz on 2007-02-15
nah, I need to install the latest JRE and link it to mozilla :/

---

### Post by phork on 2007-02-15
You should just be able to "sudo su -" to drop you into a root shell (with the root environ vars).  This is assuming that you are logged in with the user you created during your install.

---

### Post by aysiu on 2007-02-15
Try this:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

or this:
[http://www.getautomatix.com](http://www.getautomatix.com)

---

