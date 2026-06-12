---
title: "Login Message"
date: 2007-05-11
forum: General Help
---

### Post by shredfitz on 2007-05-11
Turn my computer on, get to the log-in screen and I get the following message: 


    User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and hve 644 permissions. User's $HOME directory must be owned by user and not writable by other users.


Obviously I did something. How do I amend this?


If you can help me that is great.Thank you for your time.

---

### Post by taurus on 2007-05-11
Can you post the output of this command?

```
ls -la /home
```

---

### Post by shredfitz on 2007-05-11
This is what I get:




brian@mini:~$ ls -la /home
total 12
drwxr-xr-x  3 root  root  4096 2007-05-04 18:58 .
drwxr-xr-x 23 root  root  4096 2007-05-10 09:33 ..
drwxrwxrwx 47 brian brian 4096 2007-05-11 20:07 brian

---

### Post by taurus on 2007-05-11
Try

```
cd /home
chmod 755 brian
chmod 644 ~/.dmrc
```
Reboot and see if you still get that error message about ~/.dmrc when you log in.

---

### Post by shredfitz on 2007-05-11
Great. Thank you. It went away. Mind telling me what it was, how it might have happened and what exaclty your solution made right? If not, I understand.

---

### Post by taurus on 2007-05-11
Not sure why all of a sudden the permissions of your #HOME, /home/brian & ~/.dmrc, changed unless you did that.

However, your $HOME should have a permission of 755 (read/write/execuate by you and only read and execute for group and anybody else) while ~/.dmrc should have permissions of 644 (read and write by owner, you, and read for group and everybody else).

---

