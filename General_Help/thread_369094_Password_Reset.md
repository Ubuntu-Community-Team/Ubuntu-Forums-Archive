---
title: "Password Reset"
date: 2007-02-24
forum: General Help
---

### Post by Meson on 2007-02-24
So I'd say roughly 5 minutes after I installed Ubuntu I forgot the root password.  I went into the GRUB boot menu during startup and pressed 'e' over the latest version of the kernel.  I then pressed 'e' over the next kernel line and added "single" to the end (without the quotes).  I've tried it a few times and each time the startup freezes during the splash screen.  Doing something wrong?

---

### Post by louis_nichols on 2007-02-24
The root account is not used in Ubuntu, so I'm assuming the password you forgot is the one of the first user, who has admin rights with sudo. You don't need to tweak grub to solve this. Just boot into recovery mode and when the terminal prompt shows up, enter the command:

```
passwd *username*
```

This will ask you for the new password twice. After typing it, just issue *reboot* and things should go back to normal.

---

