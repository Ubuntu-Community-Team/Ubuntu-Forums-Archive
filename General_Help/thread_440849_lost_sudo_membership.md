---
title: "lost sudo membership"
date: 2007-05-12
forum: General Help
---

### Post by bigbyte on 2007-05-12
I am the only user on my computer and was granted membership to sudo group upon installation. then I accidentally removed myself from the group using "usermod -G" instead of "usermod -a -G" while adding to another group. I tried adding myself to sudo by rebooting into safe/repair mode. Now the /etc/group shows my login in sudo group but I cannot perform any administrative functions. How can I regain admin privileges?

Thanks.

---

### Post by heimo on 2007-05-12
You're talking about sudo group, do you mean admin group? Your user should be in admin group to be able to run sudo.

---

### Post by djchandler on 2007-05-12
Have you tried the key combination "Alt-F2", entering gksu and then the command you wish to run in quotes?

For instance entering "Alt-F2" and when the dialog box appears. entering:
gksu "update-manager"
should bring up root terminal, and then the gui Update Manager. You should need to enter your original account's password for this to work

If you can't get the root terminal this way, then the following would be a last resort, and I don't recommend this in Ubuntu except in dire circumstances.

First got to this webpage
[http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way](http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way)
and follow the directions there. If this method works, should then have root privileges, and be able to re-assign your account to the administrators group. If this works, log into a normal x-window session, go to System, Administration,, then Login Window Preferences. Click the security tab, go down to security in the dialog box, and un-check Allow local administrator login if its checked, and this will once again disable the root account. If all has been successful, you should once again be able to perform administrative functions as sudo.

---

### Post by bigbyte on 2007-05-12
admin group did it.
also note that I had to remove myself from sudo group otherwise I would have too many rights and could mess with the system without entering password.

---

