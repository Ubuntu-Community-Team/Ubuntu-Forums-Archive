---
title: "ssh debug mode"
date: 2008-02-21
forum: General Help
---

### Post by anitract on 2008-02-21
I am running ssh in debug mode by using this command:
sudo /usr/sbin/sshd -d -d -d

This is supposed to "send verbose debug output to the system log, and does not put itself in the background and will only process one connection. This option is only intended for debugging for the server."

My first question is, what system log is it going to?

---

### Post by socceroos on 2008-02-21
By default on a Linux system (Ubuntu is one) SSH should log all activity to here:

/var/log/secure

Hope this helps.

---

### Post by anitract on 2008-02-22
I'm not getting ssh logging there...actually that file doesn't exist....

Other ideas?

---

### Post by anitract on 2008-02-22
Found it:
/var/log/auth.log

---

