---
title: "I Need a Password"
date: 2016-07-25
forum: General Help
---

### Post by Vincent_Massi on 2016-07-25
I intentionally set-up Xenial Xeru not to need a password. But I am learning Bash, and I need a password to use sudo. I have already tried pressing Enter, and tried using my Windows password, with no success. How can I add a password?

---

### Post by patrickkell on 2016-07-25
The traditional method to set a password is this command:
sudo passwd [user]
Where [user] is replaced with your username.
It should let you set a password without prompting for one since none currently exists.


If that doesn't work, you could type this:
su
OR
su root
THEN
passwd [user]

"su" is "switch user", which assumes root when no username is provided.
If you didn't set a root user password during install, it won't ask for one. If you did, then...hmm...I would have to research an alternative method for you.

---

### Post by Vincent_Massi on 2016-07-25
Patrick, it worked great. Thank you.

---

### Post by DuckHook on 2016-07-26
Perhaps you should tell us precisely how you installed your OS. To my knowledge, it is impossible to install without a password. Unless things have changed in Xenial, the system will not proceed with the install on a blank password. Therefore, your reference to having a blank password does not make sense to me, unless you are actually referring to the root account which is disabled by default in all flavours of 'buntu. This disabling is done for good reason, since new users run into all sorts of serious problems when they enable it.

I suspect that you may have enabled the root account through your actions and are running as root for normal use. This would be not only a huge security risk but a surefire way to mess up your user account when you actually change to running under it.

---

### Post by grahammechanical on 2016-07-26
I have not noticed any change in the installation procedures of Xenial Xerus (16.04) in comparison with earlier versions or the development version of 16.10.

We prefix commands that require administrator privileges with sudo to force a prompt for a user password. If we are working in the terminal as root then we do not need to use the word sudo. I am not recommending that we do anything to enable the root account. I am just stating a fact about our use of sudo as a prefix to a command.

Regards.

---

