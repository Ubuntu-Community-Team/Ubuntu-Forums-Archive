---
title: "change sudo user's UID"
date: 2008-05-24
forum: General Help
---

### Post by clementvii on 2008-05-24
How can I move the "sudo" user, the user who has the capability to do administrative tasks immediately after a fresh install, to a user with another UID?  It doesn't matter whether the username is transferred to the new user or not.

For example, if the new installation has a sudo user george with a UID of 1000, I'd like to create another user with a UID of 1050, make him the sudo user, and take sudo power away from the user with a UID of 1000.  It doesn't matter whether george has a UID of 1000 or 1050 after the change.

---

### Post by MythosLegend on 2008-05-24
Dude. Why did you make 2 threads on the same topic for? Your question was already answered by vor in thread
[http://ubuntuforums.org/showthread.php?t=806324](http://ubuntuforums.org/showthread.php?t=806324)

---

### Post by scxtt on 2008-05-24
the UID doesn't matter, using the current sudo user add the new user to the **admin** group.

---

### Post by rampageoberon on 2008-05-24
Ok say your current user (from the installation is george uid 1000)

so the following commands should work.

sudo adduser <newuser> --uid 1050

[fill out the appropriate data to create a new user with uid 1050]

sudo adduser <newuser> admin

[the admin group has sudo privilages so the above command will add the user to admin. You can check which group has sudo privs in the /etc/sudoers file]

Now you can remove yourself from the admin group by doing

sudo deluser george admin

[personally i'd use the new user created or root to run this command just to be safe]

Hope that helps

---

### Post by Iowan on 2008-05-24
It's possible to edit **/etc/passwd**... but it's ugly.  I did that, but then lots of permissions need to be adjusted, too. WAAAY easier to build a new user and add him/her to **admin** group.

---

### Post by clementvii on 2008-05-25
Apologies - I didn't realize I had until I read your post.  It wasn't intentional.

---

