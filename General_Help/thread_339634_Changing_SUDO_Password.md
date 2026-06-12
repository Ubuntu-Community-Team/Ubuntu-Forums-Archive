---
title: "Changing SUDO Password"
date: 2007-01-16
forum: General Help
---

### Post by Graham1 on 2007-01-16
Hi

Is it possible to change the SUDO password and if so, how?

:)

---

### Post by Littleweseth on 2007-01-16
Your password for 'sudo' is exactly the same as your normal user password (sudo authenticates *you*, your normal user self, to perform one action with elevated privileges.)

You would change it like you'd change your password normally, via the GUI dialog i'm sure exists, or by 'passwd' in a terminal.

---

### Post by Graham1 on 2007-01-16
I wasn't sure whether I had done something wrong during installation as they both had the same password. If this is normal then I'll keep as is. Thanks for your reply.

:)

---

### Post by golem3 on 2007-01-16
Go to System > Preferences > About Me  in order to change your password. Remember you login using the same password you use for SUDO. You can kill the login screen if it annoys you (like it does for me). 

You can also change it via command line 

$ passwd

if you go for $passwd -d, you can actually delete your password so hitting enter will do it (no password).

---

### Post by Littleweseth on 2007-01-16
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo) makes for good reading about the exact nature of sudo :)

-lws

---

