---
title: "Xubuntu Edgy Filesystem Permissions"
date: 2007-02-07
forum: General Help
---

### Post by nivek1385 on 2007-02-07
Okay, after a hard drive failure, I've spent the last 3 days installing a new hd, all the software I wanted (going through Synaptic A-Z after enabling several custom repos), configuring most things, installing other programs not included in repos (e.g. SeaMonkey)...well, I go to configure something within one of the user's home directories and notice that half of the user's files and directories within their home dir are owned by root (both user and group).  So, I cd to /home to take a look at all the users.  It seemed like this was a problem for more than one user.  So, while logged in under my account, I attempt to run "chown alrak2365:alrak2365 ./alrak2365" from the /home directory forgetting the sudo.  To my chagrin, it does not throw a permission error nor ask me for a password and proceeds to run the command for 3-4 minutes.  Afterwards, the ENTIRE filesystem now has ownership of alrak2365:alrak2365...  Anyone have any ideas as to 1. Why I was able to run a root-level command without root permissions, 2. Why a chown -R in /home would change the ownership of the entire filesystem, and 3. How I can fix this aside from a complete reinstall?

Thank you,
J. Kevin Hartley, Jr.

---

### Post by nivek1385 on 2007-02-07
I forgot to mention the following in my first post:

Shortly after the ownership was changed, the system locked and I was forced to restart.  Now, my administrative user no longer has sudo access and the root user is still disabled by *ubuntu default.

---

### Post by nivek1385 on 2007-02-07
Okay, I was able to use the installation CD's recovery mode to fix the overall filesystem permissions and fix my sudoers file.  However, now whenever xscreensaver locks the screen, it is impossible to unlock it, even using the same password as the user's login.  Also, passwd will not work, giving an authentication error when entering the old password.  Anyone have any ideas how to fix this?  I'm thinking it has something to do with permissions still, as I just set all file ownerships to root:root and then adjusted the /home/* as needed.  I have since noticed that certain files need to be root:shadow and adjusted a few files that way (/etc/shadow, /etc/gshadow, /usr/bin/expiry, ...).  Is there a way to find out what exactly should be set to something other than root:root or if there are any other files that need setuid root (like sudo did)?

---

