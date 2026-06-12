---
title: "noob...sudo problems...HELP!!!!!"
date: 2007-04-16
forum: General Help
---

### Post by brentcee23 on 2007-04-16
Iam a big noob and was messing around with beryl and crashed ubuntu. Now whenever I want to do anything in the terminal with Sudo I get the following

sudo: /etc/sudoers is mode 0446, should be 0440

Can anyone help or direct me in the right direction?
THANKS!!!!!!

---

### Post by taurus on 2007-04-16
Boot into recovery mode from GRUB menu and at the prompt, change the permission for /etc/sudoers.

```
chmod 440 /etc/sudoers
```
Then, reboot.

```
shutdown -r now
```

---

### Post by brentcee23 on 2007-04-16
Thank you so much, works now!

---

