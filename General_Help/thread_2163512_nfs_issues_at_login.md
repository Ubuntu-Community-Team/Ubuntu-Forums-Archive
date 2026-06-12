---
title: "nfs issues at login"
date: 2013-07-18
forum: General Help
---

### Post by gmp2 on 2013-07-18
I have been struggling for a week or so to upgrade to ubuntu 12.04.  In particular the problem I am seeing is:

         If I reboot and login as the administrator everything works.

         If I reboot and login to an account via nis (with home directory via nfs) it looks like the password is accepted, but it sends me back to the login screen (so I think it is not getting the home directory).  I login as admin, log out, and login again with the server account it works.

Does anyone have a hint where I can intelligently search for a solution.  So far my attempts are coming up empty.

Thank you!

---

### Post by DeathByDenim on 2013-07-18
You could try pressing <Ctrl> + <Alt> + 1 from the login screen to get to a terminal. If you try to login then as a normal user, it might actually show you some error messages you could use. Also, does anything show up in /var/log/syslog when you try to log in as a normal user?

---

### Post by SeijiSensei on 2013-07-18
How are user IDs handled?  It sounds like you don't have permissions to your home directory.  Do you have the same user ID locally as you do in NIS?  Being able to login as root is also evidence for an ID mismatch since root always has UID and GID zero.

Do you have access to the NIS server so you can look at its logs? I'd probably start there.

---

### Post by gmp2 on 2013-07-18
Thank you - that does confirm the problem.

I am getting a message that there is no directory.  Somehow my nfs mount is happening later now than it was in 10.04.  Is it possible that logging in as the admin triggers the mount (I have the usual information in /etc/fstab - and it does see the home directories when I log in with the local admin account).

---

### Post by gmp2 on 2013-07-18
I think it may be fixed - I used defaults in my /etc/fstab line before and changed it to spell out the options suggested.

Though I should probably test a few more times before celebrating.

Thank you for your help!


example.hostname.com:/ubuntu /local/ubuntu nfs rsize=8192,wsize=8192,timeo=14,intr

---

