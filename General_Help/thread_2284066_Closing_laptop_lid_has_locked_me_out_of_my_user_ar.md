---
title: "Closing laptop lid has locked me out of my user area"
date: 2015-06-26
forum: General Help
---

### Post by D.Lion on 2015-06-26
I was loading up Lubuntu and made the mistake of closing my laptop lid (which is set to suspend the system) before it had fully loaded. Normally the system logs me in automatically but now I am presented with a login screen when I load up. I type my password correctly and the screen goes black with a block of white writing in the top left corner, but for such a short length of time I have no chance to read what it says, and I am presented with the login screen again with no other information suggesting why I was not logged in to my user area. Selecting guest works fine, but I have no idea how to get around the guest restrictions.

Please help! Obviously I do not want the hassle of doing a fresh install if possible.

About my system:
I am using Lubuntu 32 bit version
**lsb_release -a** brings up Ubuntu 15.04
My machine is a Dell Latitude D630 with a 1.80GHz Intel Core2 Duo T7100 and 2GB RAM

---

### Post by D.Lion on 2015-06-26
I have now partially solved the problem by rebooting in recovery mode, choosing the "root shell prompt" option, backing up my data using the zip command, adding a new username using the useradd command and then rebooting and giving the new username administrator privileges. Still cant login to my original user area though.

---

### Post by Elizine on 2015-06-27
Do you mean that your password doesn't unlock the screen? Then here's what you might do -


[LIST=1]
[*]With Alt+Ctl+Backspace kill the KDM after which you should get back to the logging screen.
[*]Re-login.
[*]Go to System Settings-> Display and Monitor -> Screen Locker.
[*]After the Radio button deselect the require password and then Apply it.
[/LIST]

Hope this will help you.

---

