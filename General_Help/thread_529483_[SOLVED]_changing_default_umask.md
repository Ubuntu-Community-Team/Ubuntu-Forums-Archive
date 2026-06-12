---
title: "[SOLVED] changing default umask"
date: 2007-08-19
forum: General Help
---

### Post by nvteighen on 2007-08-19
Hi!

I've got this little and not serious problem: I'd like to set my umask to 077, so I've added "umask=077" to **my** .bashrc file (I don't care for the system's umask) and, then, rebooted to see if it worked... But when I typed umask, I got (0)022 again!

Is there something I'm missing? Thank you in advance!

---

### Post by 1/0 on 2007-08-19
How did you do change the permissions? By:

```
sudo chmod 077 .bashrc
```

path?

---

### Post by nvteighen on 2007-08-19
No, I opened .bashrc in gedit and added "umask=077" at the end of it. It's the .bashrc file in my home, so I don't need sudo.

---

### Post by 1/0 on 2007-08-19
Have you tried in terminal instead, as stated above, except the sudo then?

---

### Post by capink on 2007-08-19
I think you need to add it to .profile not .bashrc

---

### Post by nvteighen on 2007-08-20
Eureka! It was a stupid mistake by me... The solution is to add "umask 077" to ~/.bashrc, not "umask=077".

Actually, you can't do it at .profile, because it will be superseeded by the one at /etc/profile (the system default)

---

