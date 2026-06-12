---
title: "Autologin TTY without password"
date: 2019-02-05
forum: General Help
---

### Post by spookybathtub on 2019-02-05
I'm running Ubuntu server 18.04 on a USB stick for system maintenance, and I want it to auto-login as root at startup with no password.  I tried editing /etc/systemd/system/getty@.service with this line:

ExecStart=-/sbin/agetty -o '-p -- \\u' --noclear -a root %I $TERM

Now it pre-fills the username root, but it still asks for password.  What am I doing wrong?  Or would it be faster to boot directly to bash and not use getty?

---

